---
title: Сценарий делегирования удостоверений с AD FS
description: Этот сценарий описывает приложение, которому требуется доступ к внутренним ресурсам, которые требуют цепочки делегирования удостоверений для выполнения проверок управления доступом.
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 02/22/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: b82d5fd749ac874d09bc54123727aaf902c4d778
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59819855"
---
# <a name="identity-delegation-scenario-with-ad-fs"></a>Сценарий делегирования удостоверений с AD FS


[Начиная с .NET Framework 4.5, Windows Identity Foundation (WIF) полностью интегрирована в .NET Framework. Версия WIF проверялись, WIF 3.5 устарела и следует использовать только при разработке для .NET Framework 3.5 SP1 или .NET Framework 4. Дополнительные сведения о WIF в .NET Framework 4.5, также известный как WIF 4.5 см. в документации по Windows Identity Foundation в руководство по разработке .NET Framework 4.5.] 

Этот сценарий описывает приложение, которому требуется доступ к внутренним ресурсам, которые требуют цепочки делегирования удостоверений для выполнения проверок управления доступом. Цепочки делегирования удостоверений простой обычно состоит из сведения об изначальной вызывающей стороны и возможности идентификации непосредственного вызывающего объекта.

С такой модели делегирования Kerberos на платформе Windows уже сегодня внутренних ресурсов имеют доступ только к идентификатор непосредственного вызывающего объекта, а не идентична исходному вызывающему объекту. Эта модель часто называют модель доверенной подсистемы. WIF поддерживает удостоверение изначальной вызывающей стороны, а также непосредственного вызывающего объекта в цепочке делегирования, используя свойство субъекта.

На следующей схеме показана типичном сценарии делегирования удостоверения в котором Fabrikam осуществляет доступ к ресурсам, предоставляемым в приложении Contoso.com.

![идентификации](media/ad-fs-identity-delegation/id1.png)

Вымышленные пользователи, участвующие в этом сценарии являются:

- Фрэнк: Сотрудник компании Fabrikam, кто хочет получить доступ к ресурсам Contoso.
- Дэниэл: Разработчик приложения Contoso, который реализует необходимые изменения в приложении.
- Адам: Администратор ИТ-отдел Contoso.

Ниже перечислены компоненты, участвующие в этом сценарии.

- Web1: Веб-приложения с помощью ссылки к внутренним ресурсам, которые требуют делегированное удостоверение изначальной вызывающей стороны. Это приложение построено с помощью ASP.NET.
- Веб-служба, которая обращается к SQL Server, который требует делегированное удостоверение изначальной вызывающей стороны, а также для непосредственного вызывающего объекта. Эта служба создается с использованием WCF.
- sts1: STS, находится в роли поставщика утверждений и выдает утверждения, которые будут являться приложением (web1). Он устанавливает отношения доверия с помощью Fabrikam.com, а также с приложением.
- sts2: STS, который выполняет роль поставщика удостоверений, Fabrikam.com и предоставляет конечную точку, для проверки подлинности сотрудников Fabrikam. Он устанавливает отношения доверия с Contoso.com, чтобы сотрудники компании Fabrikam получают доступ к ресурсам в Contoso.com.

>[!NOTE] 
>Термин «Маркер ActAs», который часто используется в этом сценарии, ссылается на токен, выданный службой маркеров безопасности и содержит удостоверение пользователя. Свойство субъекта содержит удостоверение службы маркеров безопасности.

Как показано на предыдущей диаграмме, является поток, в этом сценарии:


1. Приложение Contoso настроен на получение маркер ActAs, содержащий сотрудника Fabrikam идентификацию как и непосредственного вызывающего объекта в свойстве субъекта. Дэниэл реализовал эти изменения в приложение.
2. Приложение Contoso настроен для передачи маркера ActAs в серверной части. Дэниэл реализовал эти изменения в приложение.
3. Contoso веб-служба настраивается для проверки маркера ActAs путем вызова sts1. Адам включил sts1 для обработки запросов.
4. Пользователь Fabrikam Фрэнк обращается к приложению Contoso и предоставляется доступ к внутренним ресурсам.

## <a name="set-up-the-identity-provider-ip"></a>Настроить поставщик удостоверений (IP)

Для администратора Fabrikam.com, Фрэнк доступны три варианта:


1. Приобретите и установите продукт с STS, например служб федерации Active Directory® (AD FS).
2. Подписаться на продукт службы маркеров безопасности облака например LiveID STS.
3. Создание собственных STS с помощью WIF.

Для этого примера мы предполагаем, что Фрэнк выбирает вариант 1 и устанавливает AD FS в качестве IP-STS. Он также настраивает конечную точку, с именем \windowsauth, для проверки подлинности пользователей. Ссылки на документацию по продукту AD FS и обращается к Adam, администратор Contoso IT, Фрэнк устанавливает отношения доверия с доменом Contoso.com.

## <a name="set-up-the-claims-provider"></a>Настройка поставщика утверждений

Параметры доступны для администратора Contoso.com, Adam, такие же, как описано выше для поставщика удостоверений. Для этого примера мы предполагаем, что Алексей выбирает вариант 1 и устанавливает AD FS 2.0 в качестве RP-STS.

## <a name="set-up-trust-with-the-ip-and-application"></a>Настройка отношения доверия с IP-адрес и приложения

Обращаясь к документации по AD FS, Адам устанавливает отношения доверия между Fabrikam.com и приложения.

## <a name="set-up-delegation"></a>Настройка делегирования

Службы федерации Active Directory обеспечивает обработку делегирования. Обращаясь к документации по AD FS, Adam позволяет обрабатывать токены ActAs.

## <a name="application-specific-changes"></a>Изменения для конкретного приложения

Для добавления поддержки делегирования удостоверений в существующее приложение необходимо сделать следующие изменения. Дэниэл использует WIF для внесения этих изменений.


- Кэш токена начальной загрузки, web1, полученные от sts1.
- Используйте CreateChannelActingAs с выданным маркером для создания канала к серверной части веб-службы.
- Вызовите метод службы серверной части.

## <a name="cache-the-bootstrap-token"></a>Кэш токена начальной загрузки

В токене начальной загрузки является начального маркера, выданного службой маркеров безопасности, а приложение извлекает утверждения из него. В нашем примере этот маркер, выданный sts1 для пользователя Фрэнка и приложение кэширует его. В следующем образце кода показано, как получить начальной загрузки маркеров в приложении ASP.NET:

```
// Get the Bootstrap Token
SecurityToken bootstrapToken = null;

IClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as IClaimsPrincipal;
if ( claimsPrincipal != null )
{
    IClaimsIdentity claimsIdentity = (IClaimsIdentity)claimsPrincipal.Identity;
    bootstrapToken = claimsIdentity.BootstrapToken;
}
```
WIF предоставляет метод, [CreateChannelActingAs](https://msdn.microsoft.com/library/ee733863.aspx), который создает канал заданного типа, который прибавляет запросы выдачи маркеров с указанным маркером безопасности как элемента ActAs. Вы можете передать токене начальной загрузки к этому методу и затем вызвать метод необходимую службу для возвращаемого канала. В этом примере сценария Фрэнка удостоверения есть [субъекта](https://msdn.microsoft.com/library/microsoft.identitymodel.claims.iclaimsidentity.actor.aspx) , имеющим значение identity web1.

В следующем фрагменте кода показан способ вызова веб-службы с [CreateChannelActingAs](https://msdn.microsoft.com/library/ee733863.aspx) и затем вызвать один из методов служб, ComputeResponse, возвращаемого канала:

```
// Get the channel factory to the backend service from the application state
ChannelFactory<IService2Channel> factory = (ChannelFactory<IService2Channel>)Application[Global.CachedChannelFactory];

// Create and setup channel to talk to the backend service
IService2Channel channel;
lock (factory)
{
// Setup the ActAs to point to the caller's token so that we perform a 
// delegated call to the backend service
// on behalf of the original caller.
    channel = factory.CreateChannelActingAs<IService2Channel>(callerToken);
}

string retval = null;

// Call the backend service and handle the possible exceptions
try
{
    retval = channel.ComputeResponse(value);
    channel.Close();
} catch (Exception exception)
{
    StringBuilder sb = new StringBuilder();
    sb.AppendLine("An unexpected exception occurred.");
    sb.AppendLine(exception.StackTrace);
    channel.Abort();
    retval = sb.ToString();
}

```
## <a name="web-service-specific-changes"></a>Изменения конкретной службы Web

Так как веб-службы построен с использованием WCF и включить для WIF, после настройки привязки с IssuedSecurityTokenParameters правильный адрес издателя, проверки ActAs автоматически обрабатываются платформой WIF. 

Веб-служба предоставляет конкретные методы, необходимые для приложения. Нет изменений конкретный код требуется в службе. В следующем образце кода показана конфигурация веб-службы с IssuedSecurityTokenParameters:

```
// Configure the issued token parameters with the correct settings
IssuedSecurityTokenParameters itp = new IssuedSecurityTokenParameters( "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" );
itp.IssuerMetadataAddress = new EndpointAddress( "http://localhost:6000/STS/mex" );
itp.IssuerAddress = new EndpointAddress( "http://localhost:6000/STS" );

// Create the security binding element
SecurityBindingElement sbe = SecurityBindingElement.CreateIssuedTokenForCertificateBindingElement( itp );
sbe.MessageSecurityVersion = MessageSecurityVersion.WSSecurity11WSTrust13WSSecureConversation13WSSecurityPolicy12BasicSecurityProfile10;

// Create the HTTP transport binding element
HttpTransportBindingElement httpBE = new HttpTransportBindingElement();

// Create the custom binding using the prepared binding elements
CustomBinding binding = new CustomBinding( sbe, httpBE );

using ( ServiceHost host = new ServiceHost( typeof( Service2 ), new Uri( "http://localhost:6002/Service2" ) ) )
{
    host.AddServiceEndpoint( typeof( IService2 ), binding, "" );
    host.Credentials.ServiceCertificate.SetCertificate( "CN=localhost", StoreLocation.LocalMachine, StoreName.My );

// Enable metadata generation via HTTP GET
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
    smb.HttpGetEnabled = true;
    host.Description.Behaviors.Add( smb );
    host.AddServiceEndpoint( typeof( IMetadataExchange ), MetadataExchangeBindings.CreateMexHttpBinding(), "mex" );

// Configure the service host to use WIF
    ServiceConfiguration configuration = new ServiceConfiguration();
    configuration.IssuerNameRegistry = new TrustedIssuerNameRegistry();

    FederatedServiceCredentials.ConfigureServiceHost( host, configuration );

    host.Open();

    Console.WriteLine( "Service2 started, press ENTER to stop ..." );
    Console.ReadLine();

    host.Close();
}
```

## <a name="next-steps"></a>Следующие шаги
[Разработка AD FS](../../ad-fs/AD-FS-Development.md)  
