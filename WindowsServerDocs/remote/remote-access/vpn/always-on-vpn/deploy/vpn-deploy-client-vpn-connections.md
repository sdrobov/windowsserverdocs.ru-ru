---
title: Настройка подключений постоянно подключенного VPN-профиля клиента Windows 10
description: На этом шаге вы Узнайте о параметрах ProfileXML и схемы и настроить клиентские компьютеры Windows 10 для взаимодействия с этой инфраструктурой с помощью VPN-подключения.
ms.prod: windows-server-threshold
ms.technology: networking-ras
ms.topic: article
ms.date: 05/29/2018
ms.assetid: d165822d-b65c-40a2-b440-af495ad22f42
ms.localizationpriority: medium
ms.author: pashort
author: shortpatti
ms.reviewer: deverette
ms.openlocfilehash: fdf640d7e98781ca054ab982027bdfe8c3fb64d6
ms.sourcegitcommit: 0948a1abff1c1be506216eeb51ffc6f752a9fe7e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2019
ms.locfileid: "66749628"
---
# <a name="step-6-configure-windows-10-client-always-on-vpn-connections"></a>Шаг 6. Настройка подключения AlwaysOn VPN для клиентов Windows 10

>Относится к: Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows 10

- [**Предыдущих:** Шаг 5. Настройка параметров DNS и брандмауэра](vpn-deploy-dns-firewall.md)<br>
- [**Далее:** Шаг 7. (Необязательно) Условный доступ для VPN-подключения с помощью Azure AD](../../ad-ca-vpn-connectivity-windows10.md)

На этом шаге вы Узнайте о параметрах ProfileXML и схемы и настроите клиентские компьютеры Windows 10 для взаимодействия с этой инфраструктурой с помощью VPN-подключения.

Можно настроить всегда на VPN-клиента через PowerShell, SCCM или Intune. Все три требуется профиль VPN в формате XML, чтобы настроить соответствующие параметры VPN. Автоматизация PowerShell регистрации для организаций без SCCM или Intune невозможно.

>[!NOTE]
>Групповая политика не поддерживает административные шаблоны для настройки клиента удаленного доступа всегда на VPN для Windows 10.  Тем не менее можно использовать сценарии входа в систему.

## <a name="profilexml-overview"></a>Общие сведения о ProfileXML

ProfileXML является узлом URI в VPNv2 CSP. Вместо настройки каждого узла VPNv2 CSP по отдельности, такие как триггеры, направлять протоколы проверки подлинности и списки — используйте этот узел, чтобы настроить клиент Windows 10 VPN, предоставляя все параметры как единый блок XML в один узел CSP. Схема ProfileXML соответствует схеме узлов VPNv2 CSP практически так же, но некоторые термины могут немного отличаться.

Используйте ProfileXML во всех методах доставки, который описывает это развертывание, включая Windows PowerShell, System Center Configuration Manager и Intune. Чтобы настроить узел ProfileXML VPNv2 CSP в этом развертывании двумя способами:

- **OMA-DM**. Один из способов является использование поставщика управления мобильными Устройствами, с помощью OMA-DM, как описано выше в разделе [VPNv2 CSP узлы](../always-on-vpn-technology-overview.md#vpnv2-csp-nodes). При использовании этого метода можно легко вставить XML-разметку конфигурации профиля VPN в ProfileXML CSP узел при использовании Intune.

- **Инструментарий управления Windows (WMI) - to - мост CSP**. Второй способ настройки узла ProfileXML CSP является использование моста WMI-CSP — класс WMI с именем **MDM_VPNv2_01**—, могут обращаться к VPNv2 CSP и узел ProfileXML. При создании нового экземпляра этого класса WMI, WMI использует CSP для создания профиля VPN, при использовании Windows PowerShell и System Center Configuration Manager.

Несмотря на то, что эти методы конфигурации различаются, в обоих случаях требуется правильно сформатированным профиля VPN в формате XML. Использование параметра ProfileXML VPNv2 CSP, создании XML с помощью схемы ProfileXML настроить теги, необходимые для развертывания простого сценария. Дополнительные сведения см. в разделе [ProfileXML XSD](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/vpnv2-profile-xsd).

Ниже можно найти все необходимые параметры и его соответствующего тега ProfileXML. Настроить каждый параметр в определенный тег в схеме ProfileXML и не все из них будут расположены в профиль машинного кода. Для размещения дополнительных тегов см. в разделе схемы ProfileXML.

[!INCLUDE [important-lower-case-true-include](../../../includes/important-lower-case-true-include.md)]

**Тип подключения:** Собственный IKEv2

Элемент ProfileXML:

```xml
<NativeProtocolType>IKEv2</NativeProtocolType>
```

**Маршрутизация.** Разделить туннелирование

Элемент ProfileXML:

```xml
<RoutingPolicyType>SplitTunnel</RoutingPolicyType>
```

**Разрешение имен:** Список сведений о имя домена и DNS-суффикс

ProfileXML элементы:

```xml
<DomainNameInformation>
<DomainName>.corp.contoso.com</DomainName>
<DnsServers>10.10.1.10,10.10.1.50</DnsServers>
</DomainNameInformation>

<DnsSuffix>corp.contoso.com</DnsSuffix>
```

**Активация:** Always On» и «доверенный сетевого обнаружения

ProfileXML элементы:

```xml
<AlwaysOn>true</AlwaysOn>
<TrustedNetworkDetection>corp.contoso.com</TrustedNetworkDetection>
```

**Проверка подлинности:** PEAP-TLS с использованием сертификатов пользователей, защищенных доверенным платформенным Модулем

ProfileXML элементы:

```xml
<Authentication>
<UserMethod>Eap</UserMethod>
<Eap>
<Configuration>...</Configuration>
</Eap>
</Authentication>
```

Простой теги можно использовать для настройки некоторых механизмов проверки подлинности VPN. Однако EAP и PEAP более сложны. — Это самый простой способ создать XML-разметку для настройки VPN-клиента с его параметрами EAP и затем экспортировать эту настройку в XML.

Дополнительные сведения о параметрах EAP см. в разделе [конфигурации EAP](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/eap-configuration).

## <a name="manually-create-a-template-connection-profile"></a>Создать профиль подключения шаблона вручную

На этом шаге вы использовать защищенный протокол проверки подлинности (PEAP) для безопасного обмена данными между клиентом и сервером. В отличие от простого имени пользователя и пароля это подключение требует уникального раздела EAPConfiguration профиля VPN для работы.

Вместо описания способ создания XML-разметку с нуля, параметры используются в Windows для создания шаблона профиля VPN. После создания шаблона профиля VPN, используйте Windows PowerShell для использования в части EAPConfiguration из клонированного шаблона для создания окончательного ProfileXML, развертываемой позже при развертывании.

### <a name="record-nps-certificate-settings"></a>Запишите параметры сертификата сервера политики сети

Прежде чем создавать шаблон, запишите имя узла или полное доменное имя (FQDN) сервера политики сети на основе сертификата сервера и имя центра сертификации, выдавшего сертификат.

**Процедура.**

1. На NPS-сервере откройте сервер политики сети.

2. В консоли сервера политики сети в разделе политики щелкните **сетевые политики**.

3. Щелкните правой кнопкой мыши **подключений виртуальной частной сети (VPN)** и нажмите кнопку **свойства**.

4. Нажмите кнопку **ограничения** , а щелкните **методы проверки подлинности**.

5. В типах EAP, нажмите кнопку **Microsoft: Защищенный EAP (PEAP)** и нажмите кнопку **изменить**.

6. Запишите значения для **сертификат, выданный** и **издателя**.

    Эти значения используются в предстоящих шаблоне конфигурации VPN. Например, если имя узла — NPS01 nps01.corp.contoso.com указано полное доменное имя сервера, имя сертификата основана на полное доменное имя или DNS-имя сервера — например, nps01.corp.contoso.com.

7. Закройте диалоговое окно редактирования свойства защищенного EAP.

8. Отмените диалоговое окно свойств подключений виртуальной частной сети (VPN).

9. Закройте сервера политики сети.

>[!NOTE]
>При наличии нескольких серверов политики сети, выполните следующие действия на каждом из них, таким образом, чтобы профиля VPN можно проверить каждый из них следует их использовать.

### <a name="configure-the-template-vpn-profile-on-a-domain-joined-client-computer"></a>Настройка шаблона профиля VPN на компьютере, присоединенном к домену

Теперь, когда у вас есть данные, необходимые настройки шаблона профиля VPN на компьютере клиента на присоединенных к домену. Тип пользователя учетной записи, которую вы использования (то есть обычный пользователь или администратор) для этой части процесса не имеет значения.

Тем не менее если еще не перезагрузку компьютера, так как Настройка автоматической регистрации сертификатов, сделайте это перед началом настройки шаблона VPN-подключение, чтобы убедиться, что у вас есть сертификат можно использовать, зарегистрированных на нем.

>[!NOTE]
>Невозможно добавление дополнительных свойств VPN, такие как правила NRPT, Always On, вручную доверенные обнаружение сети и т. д. На следующем шаге, создайте тест VPN-подключение для проверки конфигурации VPN-сервера и что можно установить VPN-подключение к серверу.

**Вручную создайте один тест VPN-подключение**

1.  Войдите на присоединенных к домену клиентский компьютер является членом **пользователей VPN** группы.

2.  В меню «Пуск» введите **VPN**, и нажмите клавишу ВВОД.

3.  В области сведений щелкните **Добавление VPN-подключения**.

4.  В списке поставщика VPN, щелкните **Windows (встроенная)** .

5.  В поле имя подключения, введите **шаблона**.

6.  В имя или адрес сервера, введите **внешних** полное ДОМЕННОЕ имя VPN-серверу (например, **vpn.contoso.com**).

7.  Нажмите кнопку **Сохранить**.

8.  В разделе связанные параметры, нажмите кнопку **изменение параметров адаптера**.

9.  Щелкните правой кнопкой мыши **шаблона**и нажмите кнопку **свойства**.

10. На **безопасности** на вкладке **тип VPN**, нажмите кнопку **IKEv2**.

11. При шифровании данных, нажмите кнопку **Максимальная стойкость шифрования**.

12. Нажмите кнопку **протокол расширенной проверки подлинности (EAP)** ; затем в **протокол расширенной проверки подлинности (EAP)** , нажмите кнопку **Microsoft: Защищенный EAP (PEAP) (шифрование включено)** .

13. Нажмите кнопку **свойства** для отображения диалогового окна Свойства защищенного EAP и выполните следующие действия:

    1. В **подключение к серверам** введите имя сервера политики сети, который вы получили из параметры проверки подлинности сервера политики сети ранее в этом разделе (например, NPS01).

    >[!NOTE]
    >Имя сервера должно соответствовать имени в сертификате. Вы восстановили это имя ранее в этом разделе. Если имя не соответствует, произойдет сбой подключения, о том, «подключение не выполнено из-за политики, настроенный на сервере удаленного доступа или VPN»

    2.  Доверенные корневые центры сертификации установите корневой ЦС, выдавшего сертификат сервера политики сети (например, contoso-CA).

    В.  В уведомления перед подключением выберите **не запрашивать пользователя авторизовать новые серверы или доверенных центров сертификации**.

    Г.  Выбрать способ проверки подлинности щелкните **смарт-карта или иной сертификат**и нажмите кнопку **Настройка**. Смарт-карты или другие свойства сертификата диалоговое окно открывается.

    Д.  Нажмите кнопку **использовать сертификат на этом компьютере**.

    f.  В окне подключения к этим серверам введите имя сервера политики сети, полученным из параметры проверки подлинности сервера политики сети на предыдущих шагах.

    ж.  Доверенные корневые центры сертификации установите корневой ЦС, выдавшего сертификат сервера политики сети.

    з.  Выберите **не запрашивать пользователя авторизовать новые серверы или доверенные центры сертификации** "флажок".

    i.  Нажмите кнопку **ОК** закрыть смарт-карты или другие свойства сертификата.

    к.  Нажмите кнопку **ОК** чтобы закрыть диалоговое окно Свойства защищенного EAP.

14. Нажмите кнопку **ОК** чтобы закрыть диалоговое окно свойств шаблона.

15. Закрытие окна сетевых подключений.

16. В параметрах, проверьте VPN-Подключение, щелкнув **шаблона**и щелкнув **Connect**.

>[!IMPORTANT]
>Убедитесь, что шаблон VPN-подключение к VPN-серверу будет успешной. Это гарантирует, что параметры EAP верны, прежде чем использовать их в следующем примере. Необходимо подключиться хотя бы один раз для продолжения; в противном случае профиль не будет содержать все сведения, необходимые для подключения к виртуальной частной сети.

## <a name="create-the-profilexml-configuration-files"></a>Создать файлы конфигурации ProfileXML

Прежде чем выполнять в этом разделе, убедитесь, что вы создал и протестировал шаблон VPN-подключение, разделе [вручную создать профиль подключения шаблона](#manually-create-a-template-connection-profile) описывает. Проверка VPN-подключение необходимо, чтобы гарантировать, что профиль содержит все сведения, необходимые для подключения к виртуальной частной сети.

Сценарий Windows PowerShell в листинге 1 создает два файла на рабочем столе, которые содержат **EAPConfiguration** теги на основании шаблона профиля подключения, созданную ранее:

- **VPN_Profile.xml.** Этот файл содержит XML-разметку, необходимые для настройки узла ProfileXML в VPNv2 CSP. Используйте этот файл с помощью MDM OMA-DM совместимых служб, таких как Intune.

- **VPN_Profile.ps1.** Этот файл является сценарий Windows PowerShell, который можно запустить на клиентских компьютерах, чтобы настроить узел ProfileXML в VPNv2 CSP. Можно также настроить CSP, развернув этот скрипт с помощью System Center Configuration Manager. Невозможно выполнить этот сценарий в сеансе удаленного рабочего стола, включая Hyper-V расширенного сеанса.

>[!IMPORTANT]
>Приведенные ниже команды примере требуется сборка Windows 10 1607 или более поздней версии.

**Создание VPN_Profile.xml и VPN_Proflie.ps1**

1. Войдите в компьютер клиента на присоединенных к домену, содержащий шаблон профиля VPN с тем же пользователем учетной записи, разделе [вручную создать профиль подключения шаблона](#manually-create-a-template-connection-profile) описано.

2. Вставьте список 1 в Windows PowerShell интегрированная среда сценариев (ISE) и настроить параметры, описанные в комментариях. Это $Template, $ProfileName, $Servers, $DnsSuffix, $DomainName, $TrustedNetwork и $DNSServers. Полное описание каждого параметра находится в комментарии.

3. Выполните скрипт, чтобы создать **VPN_Profile.xml** и **VPN_Profile.ps1** на рабочем столе.

#### <a name="listing-1-understanding-makeprofileps1"></a>Листинг 1. Основные сведения о MakeProfile.ps1

В этом разделе описывается пример кода, который можно использовать, чтобы получить представление о том, как создать профиль VPN, в частности, для настройки ProfileXML в VPNv2 CSP.

После создания сценария из этого примера кода и запустите скрипт, скрипт создает два файла: VPN_Profile.XML и VPN_Profile.ps1. Используйте VPN_Profile.xml для настройки ProfileXML в OMA-DM совместимых MDM служб, таких как Microsoft Intune.

Используйте **VPN_Profile.ps1** сценарий в Windows PowerShell или System Center Configuration Manager, чтобы настроить ProfileXML на рабочем столе Windows 10.

>[!NOTE]
>Чтобы просмотреть полный пример сценария, см. в разделе [MakeProfile.ps1 полный сценарий](#makeprofileps1-full-script).

#### <a name="parameters"></a>Параметры

Настройте следующие параметры:

**$Template**. Имя шаблона, из которого требуется извлечь конфигурацию EAP.

**$ProfileName**. Уникальный буквенно-цифровой идентификатор для профиля. Имя профиля не должно включать косую черту (/). Если имя профиля содержит пробел или другие не буквенно-цифровых символов, его необходимо правильно изолировать в соответствии со стандартом кодирования URL-адрес.

**$Servers**. Открытый или маршрутизируемый IP-адрес или DNS-имя для VPN-шлюза. Он может указывать на внешний IP-шлюз или виртуальный IP-адрес для фермы серверов. Примеры, 208.147.66.130 или vpn.contoso.com.

**$DnsSuffix**. Указывает, что один или несколько запятых, разделенные DNS-суффиксы. Первым в списке также используется как основной DNS-суффикс подключения для интерфейса VPN. Весь список, также будут добавлены в SuffixSearchList.

**$DomainName**. Используется для указания пространства имен, к которому применяется политика. При выдаче запроса на разрешение имени DNS-клиент сравнивает имя в запросе для всех пространств имен в разделе DomainNameInformationList найти совпадение. Этот параметр может принимать одно из следующих типов:

- Полное доменное имя — полное доменное имя
- Суффикс - суффикса домена, которое будет добавлено к запросу shortname для разрешения DNS. Чтобы указать суффикс, добавляйте в начало точку (.) для DNS-суффикс.

**$DNSServers**. Список с разделителями запятыми сервера IP-адрес DNS-адресов используется для пространства имен.

**$TrustedNetwork**. Строка с разделителями запятыми для идентификации доверенной сети. VPN не автоматически подключается, если пользователь находится в рамках корпоративной беспроводной сети, где защищенные ресурсы доступны непосредственно на устройство.

Ниже приведены примеры значений для параметров, используемых в приведенных ниже команд. Убедитесь, что эти значения для вашей среды.

```xml
$TemplateName = 'Template'
$ProfileName = 'Contoso AlwaysOn VPN'
$Servers = 'vpn.contoso.com'
$DnsSuffix = 'corp.contoso.com'
$DomainName = '.corp.contoso.com'
$DNSServers = '10.10.0.2,10.10.0.3'
$TrustedNetwork = 'corp.contoso.com'
```

### <a name="prepare-and-create-the-profile-xml"></a>Подготовка и создание XML-профиль

В следующем примере показан получение EAP параметров из шаблона профиля:

```xml
$Connection = Get-VpnConnection -Name $TemplateName
if(!$Connection)
{
$Message = "Unable to get $TemplateName connection profile: $_"
Write-Host "$Message"
exit
}
$EAPSettings= $Connection.EapConfigXmlStream.InnerXml
```

### <a name="create-the-profile-xml"></a>Создание XML-профиль

[!INCLUDE [important-lower-case-true-include](../../../includes/important-lower-case-true-include.md)]

```xml
$ProfileXML =
'<VPNProfile>
  <DnsSuffix>' + $DnsSuffix + '</DnsSuffix>
  <NativeProfile>
<Servers>' + $Servers + '</Servers>
<NativeProtocolType>IKEv2</NativeProtocolType>
<Authentication>
  <UserMethod>Eap</UserMethod>
  <Eap>
    <Configuration>
  '+ $EAPSettings + '
    </Configuration>
  </Eap>
</Authentication>
<RoutingPolicyType>SplitTunnel</RoutingPolicyType>
  </NativeProfile>
  <AlwaysOn>true</AlwaysOn>
  <RememberCredentials>true</RememberCredentials>
  <TrustedNetworkDetection>' + $TrustedNetwork + '</TrustedNetworkDetection>
  <DomainNameInformation>
<DomainName>' + $DomainName + '</DomainName>
<DnsServers>' + $DNSServers + '</DnsServers>
</DomainNameInformation>
</VPNProfile>'
```

### <a name="output-vpnprofilexml-for-intune"></a>VPN_Profile.xml выходные данные для Intune

Например, следующая команда можно использовать для сохранения XML-файле профиля:

```xml
$ProfileXML | Out-File -FilePath ($env:USERPROFILE + '\desktop\VPN_Profile.xml')
```

### <a name="output-vpnprofileps1-for-the-desktop-and-system-center-configuration-manager"></a>VPN_Profile.ps1 выходные данные для настольных систем и System Center Configuration Manager

В следующем примере кода настраивает канал AlwaysOn IKEv2 VPN-подключение с помощью узла ProfileXML в VPNv2 CSP.

Этот скрипт можно использовать на рабочем столе Windows 10 или в System Center Configuration Manager.

### <a name="define-key-vpn-profile-parameters"></a>Определите ключевые параметры профиля VPN

```xml
$Script = '$ProfileName = ''' + $ProfileName + '''
$ProfileNameEscaped = $ProfileName -replace ' ', '%20'
```

## <a name="define-vpn-profilexml"></a>Определение VPN ProfileXML

```xml
$ProfileXML = ''' + $ProfileXML + '''
```

### <a name="escape-special-characters-in-the-profile"></a>Пропуск специальных знаков в профиле

```xml
$ProfileXML = $ProfileXML -replace '<', '&lt;'
$ProfileXML = $ProfileXML -replace '>', '&gt;'
$ProfileXML = $ProfileXML -replace '"', '&quot;'
```

### <a name="define-wmi-to-csp-bridge-properties"></a>Определение свойств WMI-CSP моста

```xml
$nodeCSPURI = "./Vendor/MSFT/VPNv2"
$namespaceName = "root\cimv2\mdm\dmmap"
$className = "MDM_VPNv2_01"
```

### <a name="determine-user-sid-for-vpn-profile"></a>Определите идентификатор безопасности пользователя для профиля VPN:

```xml
try
{
$username = Gwmi -Class Win32_ComputerSystem | select username
$objuser = New-Object System.Security.Principal.NTAccount($username.username)
$sid = $objuser.Translate([System.Security.Principal.SecurityIdentifier])
$SidValue = $sid.Value
$Message = "User SID is $SidValue."
Write-Host "$Message"
}
catch [Exception]
{
$Message = "Unable to get user SID. User may be logged on over Remote Desktop: $_"
Write-Host "$Message"
exit
}
```

### <a name="define-wmi-session"></a>Определение сеанса WMI:

```xml
$session = New-CimSession
$options = New-Object Microsoft.Management.Infrastructure.Options.CimOperationOptions
$options.SetCustomOption("PolicyPlatformContext_PrincipalContext_Type", "PolicyPlatform_UserContext", $false)
$options.SetCustomOption("PolicyPlatformContext_PrincipalContext_Id", "$SidValue", $false)
```

### <a name="detect-and-delete-previous-vpn-profile"></a>Обнаружить и удалить предыдущий профиль VPN.

```xml
try
{
  $deleteInstances = $session.EnumerateInstances($namespaceName, $className, $options)
  foreach ($deleteInstance in $deleteInstances)
  {
    $InstanceId = $deleteInstance.InstanceID
    if ("$InstanceId" -eq "$ProfileNameEscaped")
    {
        $session.DeleteInstance($namespaceName, $deleteInstance, $options)
        $Message = "Removed $ProfileName profile $InstanceId"
        Write-Host "$Message"
    } else {
        $Message = "Ignoring existing VPN profile $InstanceId"
        Write-Host "$Message"
    }
  }
}
catch [Exception]
{
  $Message = "Unable to remove existing outdated instance(s) of $ProfileName profile: $_"
  Write-Host "$Message"
  exit
}
```

### <a name="create-the-vpn-profile"></a>Создание профиля VPN:

```xml
try
{
  $newInstance = New-Object Microsoft.Management.Infrastructure.CimInstance $className, $namespaceName
  $property = [Microsoft.Management.Infrastructure.CimProperty]::Create("ParentID", "$nodeCSPURI", "String", "Key")
  $newInstance.CimInstanceProperties.Add($property)
  $property = [Microsoft.Management.Infrastructure.CimProperty]::Create("InstanceID", "$ProfileNameEscaped", "String", "Key")
  $newInstance.CimInstanceProperties.Add($property)
  $property = [Microsoft.Management.Infrastructure.CimProperty]::Create("ProfileXML", "$ProfileXML", "String", "Property")
  $newInstance.CimInstanceProperties.Add($property)
  $session.CreateInstance($namespaceName, $newInstance, $options)
  $Message = "Created $ProfileName profile."


  Write-Host "$Message"
}
catch [Exception]
{
$Message = "Unable to create $ProfileName profile: $_"
Write-Host "$Message"
exit
}

$Message = "Script Complete"
Write-Host "$Message"'
```

### <a name="save-the-profile-xml-file"></a>Сохраните XML-файл профиля

```xml
$Script | Out-File -FilePath ($env:USERPROFILE + '\desktop\VPN_Profile.ps1')

$Message = "Successfully created VPN_Profile.xml and VPN_Profile.ps1 on the desktop."
Write-Host "$Message"
```

## <a name="makeprofileps1-full-script"></a>Полный сценарий MakeProfile.ps1

Большинство примеров с помощью командлета Set-WmiInstance Windows PowerShell для вставки в новый экземпляр класса MDM_VPNv2_01 WMI ProfileXML. 

Тем не менее это не работает в System Center Configuration Manager так, как выполнить пакет в контексте конечных пользователей. Таким образом этот скрипт использует модель CIM для создания сеанса WMI в контексте пользователя, и создает новый экземпляр класса MDM_VPNv2_01 WMI в этом сеансе. Этот класс WMI использует мост WMI-CSP для настройки VPNv2 CSP. Таким образом добавив экземпляр класса, настройке CSP. 

>[!IMPORTANT]
>Мост WMI-CSP требует прав локального администратора, намеренно. Для развертывания на профилей VPN следует использовать SCCM или управления мобильными устройствами.

>[!NOTE]
>Сценарий VPN_Profile.ps1 использует идентификатор безопасности текущего пользователя для определения контекста пользователя. Так как ИД безопасности не доступен в сеансе удаленного рабочего стола, сценарий не работает в сеансе удаленного рабочего стола. Аналогичным образом он не работает в Hyper-V расширенного сеанса. Если вы тестируете удаленного доступа всегда на VPN-Подключение на виртуальных машинах, отключите расширенного сеанса на стороне клиента виртуальных машин перед выполнением этого скрипта.

В нижеприведенном примере сценария включает в себя все примеры кода из предыдущих разделов. Убедитесь, что значения примера значениями, которые подходят для вашей среды.
    
   ```XML
    $TemplateName = 'Template'
    $ProfileName = 'Contoso AlwaysOn VPN'
    $Servers = 'vpn.contoso.com'
    $DnsSuffix = 'corp.contoso.com'
    $DomainName = '.corp.contoso.com'
    $DNSServers = '10.10.0.2,10.10.0.3'
    $TrustedNetwork = 'corp.contoso.com'

    
    $Connection = Get-VpnConnection -Name $TemplateName
    if(!$Connection)
    {
    $Message = "Unable to get $TemplateName connection profile: $_"
    Write-Host "$Message"
    exit
    }
    $EAPSettings= $Connection.EapConfigXmlStream.InnerXml
    
    $ProfileXML =
    '<VPNProfile>
      <DnsSuffix>' + $DnsSuffix + '</DnsSuffix>
      <NativeProfile>
    <Servers>' + $Servers + '</Servers>
    <NativeProtocolType>IKEv2</NativeProtocolType>
    <Authentication>
      <UserMethod>Eap</UserMethod>
      <Eap>
       <Configuration>
     '+ $EAPSettings + '
       </Configuration>
      </Eap>
    </Authentication>
    <RoutingPolicyType>SplitTunnel</RoutingPolicyType>
      </NativeProfile>
    <AlwaysOn>true</AlwaysOn>
    <RememberCredentials>true</RememberCredentials>
    <TrustedNetworkDetection>' + $TrustedNetwork + '</TrustedNetworkDetection>
      <DomainNameInformation>
    <DomainName>' + $DomainName + '</DomainName>
    <DnsServers>' + $DNSServers + '</DnsServers>
    </DomainNameInformation>
    </VPNProfile>'
    
    $ProfileXML | Out-File -FilePath ($env:USERPROFILE + '\desktop\VPN_Profile.xml')
    
    $Script = '$ProfileName = ''' + $ProfileName + '''
    $ProfileNameEscaped = $ProfileName -replace ' ', '%20'
    
    $ProfileXML = ''' + $ProfileXML + '''
    
    $ProfileXML = $ProfileXML -replace '<', '&lt;'
    $ProfileXML = $ProfileXML -replace '>', '&gt;'
    $ProfileXML = $ProfileXML -replace '"', '&quot;'
    
    $nodeCSPURI = "./Vendor/MSFT/VPNv2"
    $namespaceName = "root\cimv2\mdm\dmmap"
    $className = "MDM_VPNv2_01"
    
    try
    {
    $username = Gwmi -Class Win32_ComputerSystem | select username
    $objuser = New-Object System.Security.Principal.NTAccount($username.username)
    $sid = $objuser.Translate([System.Security.Principal.SecurityIdentifier])
    $SidValue = $sid.Value
    $Message = "User SID is $SidValue."
    Write-Host "$Message"
    }
    catch [Exception]
    {
    $Message = "Unable to get user SID. User may be logged on over Remote Desktop: $_"
    Write-Host "$Message"
    exit
    }
    
    $session = New-CimSession
    $options = New-Object Microsoft.Management.Infrastructure.Options.CimOperationOptions
    $options.SetCustomOption("PolicyPlatformContext_PrincipalContext_Type", "PolicyPlatform_UserContext", $false)
    $options.SetCustomOption("PolicyPlatformContext_PrincipalContext_Id", "$SidValue", $false)
    
        try
    {
        $deleteInstances = $session.EnumerateInstances($namespaceName, $className, $options)
        foreach ($deleteInstance in $deleteInstances)
        {
            $InstanceId = $deleteInstance.InstanceID
            if ("$InstanceId" -eq "$ProfileNameEscaped")
            {
                $session.DeleteInstance($namespaceName, $deleteInstance, $options)
                $Message = "Removed $ProfileName profile $InstanceId"
                Write-Host "$Message"
            } else {
                $Message = "Ignoring existing VPN profile $InstanceId"
                Write-Host "$Message"
            }
        }
    }
    catch [Exception]
    {
        $Message = "Unable to remove existing outdated instance(s) of $ProfileName profile: $_"
        Write-Host "$Message"
        exit
    }
    
    try
    {
        $newInstance = New-Object Microsoft.Management.Infrastructure.CimInstance $className, $namespaceName
        $property = [Microsoft.Management.Infrastructure.CimProperty]::Create("ParentID", "$nodeCSPURI", "String", "Key")
        $newInstance.CimInstanceProperties.Add($property)
        $property = [Microsoft.Management.Infrastructure.CimProperty]::Create("InstanceID", "$ProfileNameEscaped", "String", "Key")
        $newInstance.CimInstanceProperties.Add($property)
        $property = [Microsoft.Management.Infrastructure.CimProperty]::Create("ProfileXML", "$ProfileXML", "String", "Property")
        $newInstance.CimInstanceProperties.Add($property)
        $session.CreateInstance($namespaceName, $newInstance, $options)
        $Message = "Created $ProfileName profile."

        Write-Host "$Message"
    }
    catch [Exception]
    {
        $Message = "Unable to create $ProfileName profile: $_"
        Write-Host "$Message"
        exit
    }
    
    $Message = "Script Complete"
    Write-Host "$Message"'
    
    $Script | Out-File -FilePath ($env:USERPROFILE + '\desktop\VPN_Profile.ps1')
    
    $Message = "Successfully created VPN_Profile.xml and VPN_Profile.ps1 on the desktop."
    Write-Host "$Message"
   ```

## <a name="configure-the-vpn-client-by-using-windows-powershell"></a>Настройка VPN-клиента с помощью Windows PowerShell

Чтобы настроить VPNv2 CSP на клиентском компьютере Windows 10, запустите сценарий VPN_Profile.ps1 Windows PowerShell, который вы создали в [создать XML-профиль](#create-the-profile-xml) раздел. Откройте Windows PowerShell с правами администратора; в противном случае вы получите сообщение об ошибке ссылкой, _отказано в доступе_.

После выполнения VPN_Profile.ps1 для настройки профиля VPN, можно проверить в любое время что она прошла успешно, выполнив следующую команду в интегрированной среде Сценариев Windows PowerShell:

```powershell
Get-WmiObject -Namespace root\cimv2\mdm\dmmap -Class MDM_VPNv2_01
```

**Результаты без ошибок из командлета Get-WmiObject**

```powershell
__GENUS : 2
__CLASS : MDM_VPNv2_01
__SUPERCLASS:
__DYNASTY   : MDM_VPNv2_01
__RELPATH   : MDM_VPNv2_01.InstanceID="Contoso%20AlwaysOn%20VPN",ParentID
  ="./Vendor/MSFT/VPNv2"
__PROPERTY_COUNT: 10
__DERIVATION: {}
__SERVER: WIN01
__NAMESPACE : root\cimv2\mdm\dmmap
__PATH  : \\WIN01\root\cimv2\mdm\dmmap:MDM_VPNv2_01.InstanceID="Conto
  so%20AlwaysOn%20VPN",ParentID="./Vendor/MSFT/VPNv2"
AlwaysOn: True
ByPassForLocal  :
DnsSuffix   : corp.contoso.com
EdpModeId   :
InstanceID  : Contoso%20AlwaysOn%20VPN
LockDown:
ParentID: ./Vendor/MSFT/VPNv2
ProfileXML  : <VPNProfile><RememberCredentials>true</RememberCredentials>
  <AlwaysOn>true</AlwaysOn><DnsSuffix>corp.contoso.com</DnsSu
  ffix><TrustedNetworkDetection>corp.contoso.com</TrustedNetw
  orkDetection><NativeProfile><Servers>vpn.contoso.com;vpn.co
  ntoso.com</Servers><RoutingPolicyType>SplitTunnel</RoutingP
  olicyType><NativeProtocolType>Ikev2</NativeProtocolType><Au
  thentication><UserMethod>Eap</UserMethod><MachineMethod>Eap
  </MachineMethod><Eap><Configuration><EapHostConfig xmlns="h
  ttp://www.microsoft.com/provisioning/EapHostConfig"><EapMet
  hod><Type xmlns="https://www.microsoft.com/provisioning/EapC
  ommon">25</Type><VendorId xmlns="https://www.microsoft.com/p
  rovisioning/EapCommon">0</VendorId><VendorType xmlns="http:
  //www.microsoft.com/provisioning/EapCommon">0</VendorType><
  AuthorId xmlns="https://www.microsoft.com/provisioning/EapCo
  mmon">0</AuthorId></EapMethod><Config xmlns="https://www.mic
  rosoft.com/provisioning/EapHostConfig"><Eap xmlns="https://w
  ww.microsoft.com/provisioning/BaseEapConnectionPropertiesV1
  "><Type>25</Type><EapType xmlns="https://www.microsoft.com/p
  rovisioning/MsPeapConnectionPropertiesV1"><ServerValidation
  ><DisableUserPromptForServerValidation>true</DisableUserPro
  mptForServerValidation><ServerNames>NPS</ServerNames><Trust
  edRootCA>3f 07 88 e8 ac 00 32 e4 06 3f 30 f8 db 74 25 e1
  2e 5b 84 d1 </TrustedRootCA></ServerValidation><FastReconne
  ct>true</FastReconnect><InnerEapOptional>false</InnerEapOpt
  ional><Eap xmlns="https://www.microsoft.com/provisioning/Bas
  eEapConnectionPropertiesV1"><Type>13</Type><EapType xmlns="
  https://www.microsoft.com/provisioning/EapTlsConnectionPrope
  rtiesV1"><CredentialsSource><CertificateStore><SimpleCertSe
  lection>true</SimpleCertSelection></CertificateStore></Cred
  entialsSource><ServerValidation><DisableUserPromptForServer
  Validation>true</DisableUserPromptForServerValidation><Serv
  erNames>NPS</ServerNames><TrustedRootCA>3f 07 88 e8 ac 00
  32 e4 06 3f 30 f8 db 74 25 e1 2e 5b 84 d1 </TrustedRootCA><
  /ServerValidation><DifferentUsername>false</DifferentUserna
  me><PerformServerValidation xmlns="https://www.microsoft.com
  /provisioning/EapTlsConnectionPropertiesV2">true</PerformSe
  rverValidation><AcceptServerName xmlns="https://www.microsof
  t.com/provisioning/EapTlsConnectionPropertiesV2">true</Acce
  ptServerName></EapType></Eap><EnableQuarantineChecks>false<
  /EnableQuarantineChecks><RequireCryptoBinding>false</Requir
  eCryptoBinding><PeapExtensions><PerformServerValidation xml
  ns="https://www.microsoft.com/provisioning/MsPeapConnectionP
  ropertiesV2">true</PerformServerValidation><AcceptServerNam
  e xmlns="https://www.microsoft.com/provisioning/MsPeapConnec
  tionPropertiesV2">true</AcceptServerName></PeapExtensions><
  /EapType></Eap></Config></EapHostConfig></Configuration></E
  ap></Authentication></NativeProfile><DomainNameInformation>
  <DomainName>corp.contoso.com</DomainName><DnsServers>10.10.
      0.2,10.10.0.3</DnsServers><AutoTrigger>true</AutoTrigger></
  DomainNameInformation></VPNProfile>
RememberCredentials : True
TrustedNetworkDetection : corp.contoso.com
PSComputerName  : WIN01
```

Конфигурация ProfileXML должно быть верным в структуру, проверки орфографии, конфигурации и иногда регистр букв. Если вы видите что-то другой в структуре в листинге 1, скорее всего, разметка ProfileXML содержит ошибку.

Если вам необходимо устранить разметку, проще поместить его в редактор XML, чем устранять в интегрированной среде Сценариев Windows PowerShell. В любом случае начните с простой версии профиля и добавьте компоненты обратно поочередно до проблема возникает снова.

## <a name="configure-the-vpn-client-by-using-system-center-configuration-manager"></a>Настройка VPN-клиента с помощью System Center Configuration Manager

Профили VPN в System Center Configuration Manager, можно развернуть с помощью ProfileXML CSP узла, так же, как в Windows PowerShell. Здесь используется сценарий VPN_Profile.ps1 Windows PowerShell, который вы создали в разделе [создания файлов конфигурации ProfileXML](#create-the-profilexml-configuration-files).

Чтобы использовать System Center Configuration Manager для развертывания удаленного доступа всегда на профиль VPN на клиентских компьютерах Windows 10, необходимо запустить, создав группу компьютеров или пользователей, которым вы развертываете профиль. В этом случае создайте группу пользователей, чтобы развернуть скрипт конфигурации.

### <a name="create-a-user-group"></a>Создание группы пользователей

1.  В консоли Configuration Manager, откройте активы и соответствие\\коллекции пользователей.

2.  На **Главная** ленты в **создать** щелкните **создать коллекцию пользователей**.

3.  На странице "Общие" выполните следующие действия:

    1. В **имя**, тип **пользователей VPN**.

    2. Нажмите кнопку **Обзор**, нажмите кнопку **всех пользователей** и нажмите кнопку **ОК**.

    В. Нажмите кнопку **Далее**.

4.  На странице "правила членства" выполните следующие действия:

    1.  В **правила членства**, нажмите кнопку **добавить правило**и нажмите кнопку **прямое правило**. В этом примере вы добавляете отдельных пользователей на пользовательскую коллекцию. Тем не менее можно использовать правила запроса для добавления пользователей в эту коллекцию, динамически для увеличение масштаба развертывания.

    2.  На странице **приветствия** нажмите кнопку **Далее**.

    В.  На поиск страницы ресурсы в **значение**, введите имя пользователя, который вы хотите добавить. Имя ресурса содержит домен пользователя. Чтобы включить результаты на основании частичного совпадения, вставьте **%** символ на любом конце критерий поиска. Например, чтобы найти всех пользователей, содержащий строку «Лори», введите **% Лори %** . Нажмите кнопку **Далее**.

    Г.  На странице "Выбор ресурсов" выберите пользователей, необходимо добавить в группу и нажмите кнопку **Далее**.

    Д.  На странице "Сводка" нажмите кнопку **Далее**.

    f.  На последней странице нажмите кнопку **закрыть**.

6.  На странице "правила членства" мастера создания коллекции пользователей нажмите **Далее**.

7.  На странице "Сводка" нажмите кнопку **Далее**.

8.  На последней странице нажмите кнопку **закрыть**.

После создания группы пользователей для получения профиля VPN, можно создать пакет и программу для развертывания Windows PowerShell скрипт конфигурации, созданный в разделе [создания файлов конфигурации ProfileXML](#create-the-profilexml-configuration-files).

### <a name="create-a-package-containing-the-profilexml-configuration-script"></a>Создать пакет, содержащий сценарий конфигурации ProfileXML

1.  Разместите сценарий VPN_Profile.ps1 в общей сетевой папке с доступом к учетной записи компьютера сервера сайта.

2.  В консоли Configuration Manager, откройте **библиотека программного обеспечения\\управление приложениями\\пакетов**.

3.  На **Главная** ленты в **создать** щелкните **создать пакет** запуск программы мастера и создать пакет.

4.  На странице "пакет" выполните следующие действия:

    1. В **имя**, тип **Windows 10 всегда на профиль VPN**.

    2. Выберите **этот пакет содержит исходные файлы** флажок и нажмите кнопку **Обзор**.

    В. В диалоговом окне задать исходную папку, нажмите кнопку **Обзор**выберите общей папкой, содержащей VPN_Profile.ps1 и нажмите кнопку **ОК**.
        Убедитесь, что выбран сетевой путь, а не локальный путь. Другими словами, путь должен быть примерно  *\\fileserver\\vpnscript*, а не *c:\\vpnscript*.

1.  Нажмите кнопку **Далее**.

2.  На странице "тип программы", нажмите кнопку **Далее**.

3.  На странице Стандартная программа выполните следующие действия:

    1.  В **имя**, тип **сценарий профиля VPN**.

    2.  В **командной строки**, тип **PowerShell.exe - ExecutionPolicy Bypass - файл «VPN_Profile.ps1»** .

    В.  В **режим выполнения**, нажмите кнопку **запустить с правами администратора**.

    Г.  Нажмите кнопку **Далее**.

4.  На странице "требования" выполните следующие действия:

    1.  Выберите **эта программа может запускаться только на указанных платформах**.

    2.  Выберите **все Windows 10 (32-разрядная версия)** и **все Windows 10 (64-разрядная версия)** флажки.

    В.  В **место на диске**, тип **1**.

    Г.  В **максимально допустимое время выполнения (в минутах)** , тип **15**.

    Д.  Нажмите кнопку **Далее**.

5.  На странице "Сводка" нажмите кнопку **Далее**.

6.  На последней странице нажмите кнопку **закрыть**.

Пакет и программу, созданную, необходимо развернуть его в **пользователей VPN** группы.

### <a name="deploy-the-profilexml-configuration-script"></a>Развертывание скрипта конфигурации ProfileXML

1.  В консоли Configuration Manager, откройте библиотеку программного обеспечения\\управление приложениями\\пакетов.

2.  В **пакетов**, нажмите кнопку **Windows 10 всегда на профиль VPN**.

3.  На **программы** вкладку в нижней части области сведений щелкните правой кнопкой мыши **сценарий профиля VPN**, нажмите кнопку **свойства**и выполните следующие действия:

    1.  На **Дополнительно** на вкладке **при назначении этой программы на компьютере**, нажмите кнопку **один раз для каждого пользователя, входящего в систему**.

    2.  Нажмите кнопку **ОК**.

4.  Щелкните правой кнопкой мыши **сценарий профиля VPN** и нажмите кнопку **развернуть** для запуска мастера развертывания программного обеспечения.

5.  На странице "Общие" выполните следующие действия:

    1.  Рядом с **коллекции**, нажмите кнопку **Обзор**.

    2.  В **типы коллекций** (сверху слева), выберите **коллекции пользователей**.

    В.  Нажмите кнопку **пользователей VPN**и нажмите кнопку **ОК**.

    Г.  Нажмите кнопку **Далее**.

6.  На странице содержимого выполните следующие действия:

    1.  Нажмите кнопку **добавить**и нажмите кнопку **точки распространения**.

    2.  В **доступных точек распространения**, выберите точки распространения, к которым вы хотите распространить ProfileXML сценарий конфигурации, а затем нажмите кнопку **ОК**.

    В.  Нажмите кнопку **Далее**.

7.  На странице "Параметры развертывания", нажмите кнопку **Далее**.

8.  На страницу «расписания» выполните следующие действия:

    1.  Нажмите кнопку **New** чтобы открыть диалоговое окно расписания назначений.

    2.  Нажмите кнопку **назначить сразу после этого события**и нажмите кнопку **ОК**.

    В.  Нажмите кнопку **Далее**.

9.  На странице взаимодействие с пользователем выполните следующие действия:

    1.  Выберите **установки программного обеспечения** "флажок".

    2.  Нажмите кнопку **Сводка**.

10. На странице "Сводка" нажмите кнопку **Далее**.

11. На последней странице нажмите кнопку **закрыть**.

Сценарий ProfileXML конфигурации развертывания Войдите на клиентский компьютер Windows 10 с учетной записью, которую вы выбрали при создании коллекции пользователей. Проверьте конфигурацию VPN-клиента.

>[!NOTE]
>Сценарий VPN_Profile.ps1 не работает в сеансе удаленного рабочего стола. Аналогичным образом он не работает в Hyper-V расширенного сеанса. Если вы тестируете удаленного доступа всегда на VPN-Подключение на виртуальных машинах, отключите расширенного сеанса на стороне клиента виртуальных машин, прежде чем продолжить.

### <a name="verify-the-configuration-of-the-vpn-client"></a>Проверьте конфигурацию VPN-клиента

1.  В панели управления в разделе **системы\\безопасности**, нажмите кнопку **Configuration Manager**. 

2.  В диалоговом окне Свойства Configuration Manager на **действия** вкладку, выполните следующие действия:

    1.  Нажмите кнопку **цикл получения политик компьютера и оценки**, нажмите кнопку **Run Now**и нажмите кнопку **ОК**.

    2.  Нажмите кнопку **цикл получения политики пользователя и оценки**, нажмите кнопку **Run Now**и нажмите кнопку **ОК**.

    В.  Нажмите кнопку **ОК**.

3.  Закройте панель управления.

Вскоре вы должны увидеть новый профиль VPN.

## <a name="configure-the-vpn-client-by-using-intune"></a>Настройка VPN-клиента с помощью Intune

Чтобы использовать Intune для развертывания удаленного доступа всегда на профили Windows 10 VPN, можно настроить узел ProfileXML CSP с помощью профиль VPN, созданный в разделе [создания файлов конфигурации ProfileXML](#create-the-profilexml-configuration-files), или можно использовать базовый EAP Приведенный ниже образец XML.

>[!NOTE]
>Теперь Intune использует группы Azure AD. Если пользователям назначены группе пользователей VPN Azure AD Connect синхронизированы в группу пользователей VPN из локальной в Azure AD, все готово для продолжения.

Создайте политику конфигурации устройства VPN для настройки клиентских компьютеров Windows 10, для всех пользователей, добавленных в группу. Поскольку шаблон Intune предоставляет параметры VPN, копировать только \<EapHostConfig > \</EapHostConfig > часть файла VPN_ProfileXML.

### <a name="create-the-always-on-vpn-configuration-policy"></a>Создайте политику конфигурации AlwaysOn VPN

1.  Войдите в [портала Azure](https://portal.azure.com/).

2.  Перейдите к **Intune** > **конфигурации устройства** > **профили**.

3.  Нажмите кнопку **создать профиль** для запуска мастера создания профиля.

4.  Введите **имя** для профиля VPN и (необязательно) описание.

1.   В разделе **платформы**выберите **Windows 10 или более поздней версии**и выберите **VPN** из раскрывающегося списка тип профиля.

     >[!TIP]
     >Если вы создаете пользовательские profileXML VPN, см. в разделе [ProfileXML применить, с помощью Intune](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-profile-options#apply-profilexml-using-intune) инструкции.

2. В разделе **базовая VPN** Подтвердите или задайте следующие параметры:

    - **Имя подключения:** Введите имя VPN-подключение, как оно отображается на клиентском компьютере в **VPN** открыть, выбрав вкладку **параметры**, например _Contoso AutoVPN_.  
    
    - **серверы:** Добавить один или несколько VPN-серверов, щелкнув **Add.**
    
    - **Описание** и **IP-адрес или полное доменное имя:** Введите описание и IP-адрес или полное ДОМЕННОЕ имя VPN-сервера. Эти значения должны соответствовать имя субъекта в сертификате проверки подлинности VPN-сервера. 
    
    - **Сервер по умолчанию:** Если это VPN-сервера по умолчанию, равным **True**. Это позволяет использовать данный сервер как сервер по умолчанию, который устройства используют для подключения. 
    
    - **Тип подключения:** Значение **IKEv2**.  
    
    - **Always On:** Значение **включить** для подключения к VPN-Подключение автоматически при входе в систему и оставаться на связи, пока пользователь вручную отключается.
    
    - **Запоминать учетные данные при каждом входе в систему**:  Логическое значение (true или false) для кэширования учетных данных. Если задано значение true, учетные данные кэшируются в том случае, когда это возможно.

3.  Скопируйте следующую XML-строку в текстовый редактор:
 
    [!INCLUDE [important-lower-case-true-include](../../../includes/important-lower-case-true-include.md)]
    
    
    ```XML
    <EapHostConfig xmlns="https://www.microsoft.com/provisioning/EapHostConfig"><EapMethod><Type xmlns="https://www.microsoft.com/provisioning/EapCommon">25</Type><VendorId xmlns="https://www.microsoft.com/provisioning/EapCommon">0</VendorId><VendorType xmlns="https://www.microsoft.com/provisioning/EapCommon">0</VendorType><AuthorId xmlns="https://www.microsoft.com/provisioning/EapCommon">0</AuthorId></EapMethod><Config xmlns="https://www.microsoft.com/provisioning/EapHostConfig"><Eap xmlns="https://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1"><Type>25</Type><EapType xmlns="https://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV1"><ServerValidation><DisableUserPromptForServerValidation>true</DisableUserPromptForServerValidation><ServerNames>NPS.contoso.com</ServerNames><TrustedRootCA>5a 89 fe cb 5b 49 a7 0b 1a 52 63 b7 35 ee d7 1c c2 68 be 4b </TrustedRootCA></ServerValidation><FastReconnect>true</FastReconnect><InnerEapOptional>false</InnerEapOptional><Eap xmlns="https://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1"><Type>13</Type><EapType xmlns="https://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1"><CredentialsSource><CertificateStore><SimpleCertSelection>true</SimpleCertSelection></CertificateStore></CredentialsSource><ServerValidation><DisableUserPromptForServerValidation>true</DisableUserPromptForServerValidation><ServerNames>NPS.contoso.com</ServerNames><TrustedRootCA>5a 89 fe cb 5b 49 a7 0b 1a 52 63 b7 35 ee d7 1c c2 68 be 4b </TrustedRootCA></ServerValidation><DifferentUsername>false</DifferentUsername><PerformServerValidation xmlns="https://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">true</PerformServerValidation><AcceptServerName xmlns="https://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">true</AcceptServerName></EapType></Eap><EnableQuarantineChecks>false</EnableQuarantineChecks><RequireCryptoBinding>false</RequireCryptoBinding><PeapExtensions><PerformServerValidation xmlns="https://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV2">true</PerformServerValidation><AcceptServerName xmlns="https://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV2">true</AcceptServerName></PeapExtensions></EapType></Eap></Config></EapHostConfig>
    ```

4.  Замените  **\<TrustedRootCA > 5а 89 fe cb 5b 49 a7 0b 1a 52 63 b7 35 ee d7 1c c2 68 быть 4b <\/TrustedRootCA >** в примере на отпечаток сертификата корневого центра сертификации на предприятии в обоих местах.
  
    >[!Important]
    >Не используйте пример отпечатка в \<TrustedRootCA >\</TrustedRootCA > разделе ниже.  TrustedRootCA должен быть отпечаток в локальной корневой центр сертификации, выдавший сертификат проверки подлинности сервера RRAS и NPS-серверов. **Это не должно быть в облаке корневого сертификата, а также промежуточные отпечаток сертификата выдающего ЦС**.

5.  Замените  **\<ServerNames > NPS.contoso.com\</ServerNames >** в образце XML полным доменным именем NPS присоединенных к домену, где будет выполнена проверка подлинности. 

6.  Скопируйте измененный XML-строку и вставьте в **XML-файл EAP** на вкладке базовая VPN и нажмите кнопку **ОК**.
    В Intune создается политика всегда в конфигурации VPN-устройства, с помощью EAP.


### <a name="sync-the-always-on-vpn-configuration-policy-with-intune"></a>Синхронизировать политики конфигурации AlwaysOn VPN с помощью Intune

Чтобы проверить политики конфигурации, войдите в клиентский компьютер Windows 10 как пользователь добавленные **всегда работают пользователи VPN** группы, а затем синхронизации с Intune.

1.  В меню «Пуск» выберите **параметры**.

2.  В разделе параметров щелкните **учетные записи**и нажмите кнопку **доступ к рабочей или учебной**.

3.  Выберите профиль управления мобильными Устройствами и нажмите кнопку **Info**.

4.  Нажмите кнопку **синхронизации** для принудительного вычисления политики Intune и извлечения.

5.  Закрыть диалоговое окно "Параметры". После синхронизации вы увидите доступные профиля VPN на компьютере.

## <a name="next-steps"></a>Следующие шаги

Завершено развертывание AlwaysOn VPN.  Другие функции, которые можно настроить см. в следующей таблице:

|Если вы хотите...  |Затем просмотрите...  |
|---------|---------|
|Настройка условного доступа для VPN    |[Шаг 7. (Необязательно) Настройка условного доступа для VPN-подключения с помощью Azure AD](../../ad-ca-vpn-connectivity-windows10.md): На этом шаге можно точно настроить доступ авторизованных пользователей VPN ресурсы с помощью [условного доступа Azure Active Directory (Azure AD)](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). С помощью условного доступа Azure AD для подключения к виртуальной частной сети (VPN) можно защитить VPN-подключений. Условный доступ — это модуль оценки на основе политик, который позволяет создавать правила доступа для любого приложения, подключенного к Azure Active Directory (Azure AD).         |
|Дополнительные сведения о дополнительных возможностях VPN  |[Дополнительные функции VPN](always-on-vpn-adv-options.md#advanced-vpn-features): Эта статья содержит рекомендации о Включение фильтров трафика VPN, как настроить автоматическое VPN-подключений, с помощью триггеров приложения и способы настройки сервера политики сети, чтобы разрешить VPN-подключений только от клиентов, использующих сертификаты, выданные Azure AD.        |
