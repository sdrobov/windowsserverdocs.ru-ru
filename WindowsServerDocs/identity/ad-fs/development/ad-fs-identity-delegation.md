---
title: "Сценарий делегирования удостоверения со службами AD FS"
description: "Этот сценарий описывает приложение, которое требуется доступ к внутренние ресурсы, которые требуют цепочки делегирования удостоверений для выполнения проверок управления доступом."
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 02/22/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: b82d5fd749ac874d09bc54123727aaf902c4d778
ms.sourcegitcommit: c16a2bf1b8a48ff267e71ff29f18b5e5cda003e8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2018
---
# <a name="identity-delegation-scenario-with-ad-fs"></a>Сценарий делегирования удостоверения со службами AD FS


[Начиная с .NET Framework 4.5, Windows Identity Foundation (WIF) полностью интегрирована в .NET Framework. Версия WIF, описанная в этом разделе в WIF 3.5 устарела и должна использоваться только при разработке для .NET Framework 3.5 SP1 или .NET Framework 4. Дополнительные сведения о WIF в .NET Framework 4.5, также известные как WIF 4.5, см. в документации Windows Identity Foundation в руководстве по разработке .NET Framework 4.5.] 

Этот сценарий описывает приложение, которое требуется доступ к внутренние ресурсы, которые требуют цепочки делегирования удостоверений для выполнения проверок управления доступом. Цепочки делегирования удостоверений простых обычно состоит из сведения о начальной вызывающей стороны и удостоверения непосредственной вызывающей стороны.

Модель делегирования Kerberos на платформе Windows уже сегодня ресурсы внутренних имеют доступ только к удостоверение непосредственной вызывающей стороны и не, начальной вызывающей стороны. Эта модель часто называется моделью доверенной подсистемы. WIF поддерживает удостоверение начальной вызывающей стороны, а также для непосредственной вызывающей стороны в цепочке делегирования, используя свойство субъект.

На следующей схеме показана сценарий делегирования удостоверения типичные, ресурсов, предоставляемых в приложении Contoso.com обращается к сотрудников Fabrikam.

![Удостоверение](media/ad-fs-identity-delegation/id1.png)

Ниже перечислены вымышленные пользователи, участвующие в этом сценарии

- Алексей: Fabrikam сотрудник, который хочет получить доступ к ресурсам Contoso.
- Дэниел: Contoso приложения разработчика, который реализует необходимые изменения в приложении.
- Адам: Contoso ИТ-администратор.

Ниже перечислены компоненты, участвующие в этом сценарии

- Web1: веб-приложения со ссылками на внутренние ресурсы, которые требуют делегированные удостоверение начальной вызывающей стороны. Это приложение создается с помощью ASP.NET.
- Веб-службы, которое получает доступ к SQL Server, требующий делегированные удостоверение начальной вызывающей стороны, а также для непосредственной вызывающей стороны. Эта служба, созданной с помощью WCF.
- sts1: STS в роли поставщика утверждений, который выдает утверждения, которые ожидаются в приложении (web1). Он установил отношения доверия с Fabrikam.com, а также с приложением.
- sts2: STS, в роли поставщика удостоверений для Fabrikam.com и предоставляет конечной точки, сотрудник Fabrikam использует для проверки подлинности. Он установил отношения доверия с Contoso.com, чтобы разрешить доступ к ресурсам с Contoso.com сотрудники компании Fabrikam.

>[!NOTE] 
>Термин «ActAs маркер», которая часто используется в этом сценарии, относится к токен, который выдан STS и содержит удостоверение пользователя. Свойство субъект содержит STS удостоверений.

Как показано на рисунке выше, является поток, в этом сценарии:


1. Приложение Contoso настроено для получения маркера ActAs, содержащий сотрудников Fabrikam идентификацию как и непосредственной вызывающей стороны в свойстве субъект. Дэниел реализовала этих изменений в приложение.
2. Приложение Contoso настроен для передачи маркера ActAs внутренней службы. Дэниел реализовала этих изменений в приложение.
3. Contoso веб-служба настроена для проверки маркера ActAs путем вызова sts1. Адам включил sts1 для обработки запросов.
4. Пользователь Fabrikam Алексей обращается к приложения Contoso и предоставляется доступ к ресурсам сервера.

## <a name="set-up-the-identity-provider-ip"></a>Настройка поставщика удостоверений (IP)

Для администратора Fabrikam.com, Михаил доступны три варианта:


1. Приобретите и установите продукт токенов безопасности, например службы федерации Active Directory® (AD FS).
2. Подписаться на продукт STS облака, например LiveID STS.
3. Создание собственных WIF с помощью STS.

Для этого примера сценария мы предполагается, что Михаил выбирает вариант 1 и устанавливает AD FS в IP-STS. Он также настраивает конечной точки, с именем \windowsauth для проверки подлинности пользователей. Путем обращения к документации по продукту AD FS и обращается к Adam Contoso ИТ-администратор Михаил устанавливает отношения доверия с доменом Contoso.com.

## <a name="set-up-the-claims-provider"></a>Настройка поставщика утверждений

Параметры доступны для администратора Contoso.com, Adam, такие же, как описано ранее для поставщика удостоверений. Для этого примера сценария мы предполагается, что Adam выбирает вариант 1 и устанавливает в качестве RP-STS AD FS 2.0.

## <a name="set-up-trust-with-the-ip-and-application"></a>Настройка доверия IP-адрес и приложения

Путем обращения к документации по AD FS, Адам устанавливает отношения доверия между Fabrikam.com и приложения.

## <a name="set-up-delegation"></a>Настройка делегирования

AD FS обеспечивает обработку делегирования. Путем обращения к документации по AD FS, Адам позволяет обрабатывать ActAs маркеров.

## <a name="application-specific-changes"></a>Изменения для конкретного приложения

Чтобы добавить поддержку для делегирования удостоверений в существующее приложение осуществляются следующие изменения. Дэниел использует WIF для внесения этих изменений.


- Кэширование загрузочный маркера, web1, полученные от sts1.
- Используйте CreateChannelActingAs с выданный маркер для создания канала для веб-службы внутренних.
- Вызовите метод внутренней службы.

## <a name="cache-the-bootstrap-token"></a>Кэширование загрузочный маркера

Маркер загрузочный является начальной маркера, выданного службой токенов безопасности, и приложение извлекает утверждения из него. В этом сценарии примере этот маркер выдан sts1 для пользователя Михаил и приложение выполнит его кэширование. В следующем примере кода показано, как получить для начальной загрузки маркера в приложении ASP.NET:

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
WIF предоставляет метод, [CreateChannelActingAs](https://msdn.microsoft.com/library/ee733863.aspx), который создает канал указанного типа, который расширяет запросы на выпуск маркера с маркером безопасности, как элемент ActAs. Можно передавать маркер начальной загрузки этого метода и затем вызвать метод необходимые службы, возвращаемых канала. В этом примере, удостоверение Алексей имеет [субъект](https://msdn.microsoft.com/library/microsoft.identitymodel.claims.iclaimsidentity.actor.aspx) удостоверению web1 в наборе свойств.

В следующем фрагменте кода показано, как вызывать веб-службу с [CreateChannelActingAs](https://msdn.microsoft.com/library/ee733863.aspx) и затем вызовите один из методов служб, ComputeResponse, возвращенный канала:

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
## <a name="web-service-specific-changes"></a>Изменения специфичными для службы Web

Поскольку веб-службы, созданный с помощью WCF и включить WIF, настроив привязку с IssuedSecurityTokenParameters с соответствующими адреса поставщика, проверки ActAs автоматически обрабатывается WIF. 

Веб-служба предоставляет особые методы, требуемые для приложения. Отсутствуют изменения кода требуются службы. В следующем примере кода показана конфигурация веб-службы с IssuedSecurityTokenParameters:

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

## <a name="next-steps"></a>Дальнейшие действия
[Разработка AD FS](../../ad-fs/AD-FS-Development.md)  
