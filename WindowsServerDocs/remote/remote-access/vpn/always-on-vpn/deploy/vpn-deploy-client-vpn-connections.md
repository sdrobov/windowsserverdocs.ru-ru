---
title: Настройка подключений постоянно подключенного VPN-профиля клиента Windows 10
description: На этом этапе вы Узнайте о параметрах ProfileXML и схемы и настройка клиентских компьютеров Windows 10 для связи с ИТ-инфраструктуры с VPN-подключение.
ms.prod: windows-server-threshold
ms.technology: networking-ras
ms.topic: article
ms.date: 05/29/2018
ms.assetid: d165822d-b65c-40a2-b440-af495ad22f42
ms.localizationpriority: medium
ms.author: pashort
author: shortpatti
ms.reviewer: deverette
ms.openlocfilehash: 6b383076686092e20448977bed3766f7d7d1c2b8
ms.sourcegitcommit: 4147e092d77d9458696e6686bccefe3788c90508
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/28/2019
ms.locfileid: "9031318"
---
# Шаг6. Настройка подключений VPN клиент Windows 10

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows 10


& #171;  [ **Предыдущих:** шаг 5. Настройка параметров брандмауэра и DNS](vpn-deploy-dns-firewall.md)<br>
& #187; [ **Далее:** шаг 7. (Необязательно) Условного доступа для VPN-подключения с помощью Azure AD](../../ad-ca-vpn-connectivity-windows10.md)

На этом этапе вы Узнайте о параметрах ProfileXML и схемы и настройка клиентских компьютеров Windows 10 для связи с ИТ-инфраструктуры с VPN-подключение. 

Вы можете настроить клиент VPN через PowerShell, SCCM или Intune. Все три требуется профиль VPN XML-ФАЙЛ для настройки соответствующие параметры VPN. Автоматизация PowerShell регистрации для организаций без SCCM или Intune возможна.

>[!NOTE]
>Групповая политика не включает административных шаблонов для настройки Windows10 удаленного доступа всегда на VPN-клиент.  Тем не менее можно использовать сценарии входа в систему.

## Общие сведения о ProfileXML

ProfileXML представляет собой узел URI в VPNv2 CSP. Вместо настройки каждого узла VPNv2 CSP по отдельности, например триггеров, маршрута списков и протоколов проверки подлинности — использовать этот узел для настройки Windows10 VPN-клиент, предоставляя все параметры как единый блок XML-ФАЙЛ на один узел CSP. ProfileXML схема соответствует схеме узлы VPNv2 CSP практически так же, но некоторые условия немного отличаются.

Используйте ProfileXML в все методы доставки, которые описаны развертывания, включая Windows PowerShell, System Center Configuration Manager и Intune. Настройка узел ProfileXML VPNv2 CSP в это развертывание двумя способами:

- **OMA-DM**. Один из способов — использовать поставщика MDM с помощью OMA-DM, как описано выше в разделе [узлы VPNv2 CSP](../always-on-vpn-technology-overview.md#vpnv2-csp-nodes). При использовании этого метода можно легко вставить разметки XML-ФАЙЛ конфигурации профиля VPN в узел ProfileXML CSP при использовании Intune.

- **Инструментарий управления Windows (WMI) - to - мост CSP**. Второй способ настройки узел ProfileXML CSP — использовать мост WMI-CSP — класс WMI с именем **MDM_VPNv2_01**, который можно получить доступ к VPNv2 CSP и узел ProfileXML. Когда вы создаете новый экземпляр этого класса WMI, WMI использует CSP для создания профиля VPN при использовании System Center Configuration Manager и Windows PowerShell.

Несмотря на то, что эти методы конфигурации отличаются, в обоих случаях требуется правильно отформатированный XML-ФАЙЛ VPN-профиль. Использовать параметр ProfileXML VPNv2 CSP, создать XML-ФАЙЛ с помощью ProfileXML схемы для настройки теги, необходимые для сценария простого развертывания. Дополнительные сведения см. в разделе [ProfileXML XSD-ФАЙЛ](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/vpnv2-profile-xsd).

Ниже представлен всех необходимых параметров и его соответствующий тег ProfileXML. Настройка каждого параметра в определенный тег в схеме ProfileXML, а не все из них можно найти в разделе собственный профиль. Размещение дополнительных тегов см. в разделе схемы ProfileXML.

[!INCLUDE [important-lower-case-true-include](../../../includes/important-lower-case-true-include.md)]

**Тип подключения:** Собственные IKEv2

ProfileXML элемент:

    <NativeProtocolType>IKEv2</NativeProtocolType>

**Маршрутизации:** Разделение туннелирование

ProfileXML элемент:

    <RoutingPolicyType>SplitTunnel</RoutingPolicyType>

**Разрешение имен:** Список сведений о домене и DNS-суффикс

ProfileXML элементы:

    <DomainNameInformation>
    <DomainName>.corp.contoso.com</DomainName>
    <DnsServers>10.10.1.10,10.10.1.50</DnsServers>
    </DomainNameInformation>
    
    <DnsSuffix>corp.contoso.com</DnsSuffix>


**Активирующего:** Обнаружение всегда включено и доверенной сети

ProfileXML элементы:

    <AlwaysOn>true</AlwaysOn>
    <TrustedNetworkDetection>corp.contoso.com</TrustedNetworkDetection>


**Проверки подлинности:** Протокол PEAP-TLS с сертификатами пользователя, защищенного с помощью доверенного платформенного МОДУЛЯ

ProfileXML элементы:

    <Authentication>
    <UserMethod>Eap</UserMethod>
    <Eap>
    <Configuration>...</Configuration>
    </Eap>
    </Authentication>

Простой теги можно использовать для настройки некоторые механизмы проверки подлинности VPN. Тем не менее PEAP и EAP более трудоемки. Самый простой способ создать XML-разметку стоит настроить VPN-клиент с ее параметры EAP, а затем экспортировать эту конфигурацию в XML-ФАЙЛЕ. 

Дополнительные сведения о параметрах EAP см. в разделе [Конфигурация EAP](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/eap-configuration). 

## <a name="bkmk_profile"></a>Создание профиля подключения шаблона вручную

На этом этапе используемого \(PEAP\) защищенный протокол EAP для обеспечения безопасного обмена данными между клиентом и сервером. В отличие от имени простого пользователя и пароль это подключение требуется уникальный раздел EAPConfiguration в профиле VPN для работы. 

Вместо которых описано, как создать XML-разметку с нуля, используйте параметры в Windows для создания шаблона профиля VPN. После создания шаблона профиля VPN, использовать Windows PowerShell для использования его часть EAPConfiguration на основе этого шаблона для создания окончательного ProfileXML при развертывании позже в развертывании.

### Запишите параметры сертификата сервера политики сети

Перед созданием шаблона, запишите имя узла или полное доменное имя (FQDN) сервера политики сети в сертификата сервера и имя центра сертификации, выпустившего сертификат.

**Процедура:**

1.  К ресурсам сервера политики сети откройте сервера политики сети.

2.  В консоли сервера политики сети политики, установите для **Политики сети**.

3.  Щелкните правой кнопкой мыши **\(VPN\) подключений виртуальной частной сети**и нажмите кнопку **Свойства**.

4.  Перейдите на вкладку **ограничения** и нажмите кнопку **Методы проверки подлинности**.

5.  В типы EAP, выберите **Майкрософт: защищенный EAP (PEAP)** и нажмите кнопку **Изменить**.

6.  Запишите значения **выдан сертификат** и **издателя**.<p>Используйте эти значения в ближайшие шаблона конфигурации VPN. Например если полное доменное имя сервера — nps01.corp.contoso.com и NPS01 — это имя узла, имя сертификата основана на полное доменное имя и DNS-имя сервера — например, nps01.corp.contoso.com.

7.  Закройте диалоговое окно Изменить свойства защищенного EAP.

8.  Закройте диалоговое окно свойств подключений виртуальной частной сети (VPN).

9.  Закройте сервера политики сети.

>[!NOTE]
>При наличии нескольких серверов политики сети, выполните следующие действия для каждого из них, чтобы VPN-профиля можно проверить каждый из них следует их использовать.

### Настройка шаблона профиля VPN на domain\ к домену клиентский компьютер

Теперь у вас есть сведения, необходимые Настройка шаблона профиля VPN на присоединенный к домену клиентский компьютер. Тип учетной записи пользователя, используемого \ (т.е., обычный пользователь или administrator\) для этой части процесса, не имеет значения. 

Тем не менее если вы еще не перезагрузку компьютера с момента Настройка автоматической регистрации сертификатов, сделать перед настройкой шаблоне VPN-подключение, чтобы убедиться, что у вас есть зарегистрированные на нем можно было использовать сертификат.

>[!NOTE]
>Не существует способа вручную добавить дополнительных свойств VPN, например NRPT правила, всегда включен, доверенные обнаружения сети и т. д. В следующем шаге, вы создаете проверить подключение VPN для проверки конфигурации VPN-сервера и что вы можете создать VPN-подключение к серверу.

**Вручную создайте единый тест VPN-подключение**

1.  Войдите в присоединенный к домену клиентский компьютер как член группы **Пользователей VPN** .

2.  В меню "Пуск" введите **VPN**и нажмите клавишу ВВОД.

3.  В области сведений нажмите кнопку **Добавить VPN-подключение**.

4.  В списке VPN поставщик выберите **Windows (встроенной)**.

5.  В имени подключения введите **шаблон**.

6.  В имя или адрес сервера, введите **внешний** полное доменное имя сервера VPN \ (например,**vpn.contoso.com**\).

7.  Нажмите кнопку **Сохранить**.

8.  В разделе соответствующих страниц параметров выберите **Изменить параметры адаптера**.

9.  Щелкните правой кнопкой мыши **шаблон**и нажмите кнопку **Свойства**.

10. На вкладке " **Безопасность** ", в **Тип VPN**щелкните **IKEv2**.

11. В шифрования выберите **Максимальное надежности шифрования**.

12. Выберите **Протокол расширенной проверки подлинности (EAP)**; Выберите из **Расширяемый протокол проверки подлинности (EAP)**, **Майкрософт: защищенный EAP (PEAP) (шифрование включено)**.

13. Щелкните **Свойства** , чтобы открыть диалоговое окно Свойства защищенного EAP и выполните следующие действия:

    А. В поле **подключаться к серверам** введите имя сервера политики сети, полученные из параметров проверки подлинности сервера политики сети ранее в этом разделе (например, NPS01).

    >[!NOTE]
    >Имя сервера, которое вы вводите должно соответствовать имени в сертификате. Восстановить это имя этого раздела. Если имя не совпадают, подключение завершится ошибкой, сообщающую о том, «подключение не выполнено из-за политика, настроенная на сервере удаленного доступа или VPN»

    Б.  В разделе доверенных корневых центров сертификации выберите корневого центра сертификации, выпустившего сертификат сервера политики сети (например, contoso-CA).

    в.  В уведомления до подключения выберите **не запрашивайте пользователя авторизовать новые серверы или доверенных центров сертификации**.

    г.  Выберите метод проверки подлинности нажмите кнопку **смарт-карта или другой сертификат**, а затем **настроить**. Откроется смарт-карты или другие свойства сертификата диалоговое окно.

    д.  Щелкните **использовать сертификат на этом компьютере**.

    е.  В поле подключиться к этим серверам введите имя сервера политики сети, полученные из параметров проверки подлинности сервера политики сети в предыдущих шагах.

    ж.  В разделе доверенных корневых центров сертификации выберите корневого центра сертификации, выпустившего сертификат сервера политики сети.

    з.  Выберите **не запрашивать пользователя авторизовать новые серверы или доверенные центры сертификации** флажок.

    i.  Нажмите кнопку **ОК** , чтобы закрыть смарт-карты или другое диалоговое окно свойств сертификата.

    j.  Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно Свойства защищенного EAP.

10. Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно свойств шаблона.

11. Закройте окно сетевых подключений.

12. В параметрах протестируйте VPN, выбрав **шаблон**и **Connect**.

>[!IMPORTANT]
>Убедитесь, что он шаблоне VPN-подключения VPN-сервер. Это гарантирует, что параметры EAP указаны правильно, прежде чем использовать их в следующем примере. Необходимо подключить по крайней мере один раз перед продолжением; в противном случае профиль не будет содержать все сведения, необходимые для подключения к VPN.

## <a name="bkmk_ProfileXML"></a>Создайте файлы конфигурации ProfileXML

Перед выполнением в этом разделе, убедитесь, что вы создали и протестированными шаблоне VPN-подключение, описывающий разделе [вручную создать профиль подключения шаблона](#bkmk_profile) . Тестирование VPN-подключение необходимо убедиться, что профиль содержит все сведения, необходимые для подключения к VPN.

Сценарий Windows PowerShell в описании 1 создает два файла на рабочем столе, которые содержат теги **EAPConfiguration** на основе профиля подключения шаблон, созданный ранее.

-   **VPN_Profile.XML.** Этот файл содержит разметку XML, необходимые для настройки узел ProfileXML в VPNv2 CSP. Используйте этот файл с помощью служб OMA-DM совместимые с MDM, например Intune.

-   **VPN_Profile.ps1.** Этот файл — сценарий Windows PowerShell, который можно запустить на клиентских компьютерах для настройки узел ProfileXML в VPNv2 CSP. Вы также можете настроить CSP путем развертывания этот сценарий с помощью System Center Configuration Manager. Этот сценарий не удается выполнить во время сеанса удаленного рабочего стола, включая Hyper-V расширенного сеанса.

>[!IMPORTANT]
>Приведенные ниже команды примере требуется сборки Windows 10, 1607 или более поздней версии.

**Создание VPN_Profile.xml и VPN_Proflie.ps1**

1. Войдите в присоединенный к домену клиентский компьютер, на котором шаблона профиля VPN с тем же пользователем учетной записи, раздел «Вручную создать профиль подключения шаблон» описано.

2. Вставить список 1 в интегрированной среде сценариев Windows PowerShell \(ISE\) и настроить параметры, описанные в комментарии. Это $Template, $ProfileName, $Servers, $DnsSuffix, $DomainName, $TrustedNetwork и $DNSServers. Подробное описание каждого параметра находится в комментарии.

3.  Запустите сценарий для создания **VPN_Profile.xml** и **VPN_Profile.ps1** на рабочем столе.

#### Пример 1. Общие сведения о MakeProfile.ps1

В этом разделе объясняется в примере кода, который можно использовать для получения сведения о том, как создать профиль VPN, в частности, для настройки ProfileXML в VPNv2 CSP.

После того как собрать сценария в этом примере кода и запустить сценарий, сценарий создает два файла: VPN_Profile.xml и VPN_Profile.ps1. Используйте VPN_Profile.xml для настройки ProfileXML OMA-DM совместимые MDM службы, такие как Microsoft Intune.

Используйте сценарий **VPN_Profile.ps1** в Windows PowerShell или System Center Configuration Manager для настройки ProfileXML на рабочем столе Windows 10.

>[!NOTE]
>Чтобы просмотреть полный пример сценария, см. в разделе [MakeProfile.ps1 полный скрипт](#bkmk_fullscript).

#### Параметры

Настройте следующие параметры:

**$Template**. Имя шаблона, из которого требуется получить конфигурации EAP.

**$ProfileName**. Уникальный буквенно-цифровой идентификатор для профиля. Имя профиля не должен содержать косая черта (/). Если имя профиля содержит пробел или другие не буквенно-цифровых символов, его необходимо правильно экранировать согласно стандарту кодирования URL-адрес.

**$Servers**. Открытый или маршрутизируемый IP-адрес или DNS-имя VPN-шлюза. Он может указывать на внешний IP-адрес шлюза или виртуальный IP-адрес фермы серверов. Примеры, 208.147.66.130 или vpn.contoso.com.

**$DnsSuffix**. Указывает, что один или несколько запятыми запятыми суффиксов DNS. Первый элемент в списке также используется как основной DNS-суффикс подключения для интерфейса VPN. Полный список также будут добавлены в SuffixSearchList.

**$DomainName**. Используется для указания пространства имен, к которому применяется политика. Когда отдается запрос имени, DNS-клиент сравнивает имя в для всех пространств имен в разделе DomainNameInformationList для поиска соответствующего запроса. Этот параметр может принимать одно из следующих типов:

- Полное доменное имя - полное доменное имя
- Суффикс - суффикс домена, которые будут добавлены в запрос короткое имя для разрешения DNS. Указание суффикса, добавьте префикс точку \ (.) в DNS-суффикс.

**$DNSServers**. Список разделенных запятой IP-сервера DNS-адресов используйте для пространства имен.

**$TrustedNetwork**. Разделенный запятыми строка определить доверенную сеть. VPN не подключаться автоматически когда пользователь находится в корпоративной беспроводной сети, где защищенные ресурсы доступны непосредственно на устройство.

Вот пример значения для параметров, используемых в приведенные ниже команды. Убедитесь, что эти значения для вашей среды.

    $TemplateName = 'Template'
    $ProfileName = 'Contoso AlwaysOn VPN'
    $Servers = 'vpn.contoso.com'
    $DnsSuffix = 'corp.contoso.com'
    $DomainName = '.corp.contoso.com'
    $DNSServers = '10.10.0.2,10.10.0.3'
    $TrustedNetwork = 'corp.contoso.com'


### Подготовка и создать XML-ФАЙЛ профиля

Следующий пример команды получить настройки EAP из шаблона профиля:


    $Connection = Get-VpnConnection -Name $TemplateName
    if(!$Connection)
    {
    $Message = "Unable to get $TemplateName connection profile: $_"
    Write-Host "$Message"
    exit
    }
    $EAPSettings= $Connection.EapConfigXmlStream.InnerXml


### Создание XML-ФАЙЛ профиля

[!INCLUDE [important-lower-case-true-include](../../../includes/important-lower-case-true-include.md)]

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


### VPN_Profile.xml выходные данные для Intune

В следующем примере командная можно использовать для сохранения XML-файл профиля:

    $ProfileXML | Out-File -FilePath ($env:USERPROFILE + '\desktop\VPN_Profile.xml')

### VPN_Profile.ps1 выходные данные для рабочего стола и System Center Configuration Manager

В следующем примере кода настраивает AlwaysOn IKEv2 VPN-подключение с помощью узел ProfileXML в VPNv2 CSP.

Можно использовать этот сценарий на рабочем столе Windows 10 или в System Center Configuration Manager.

### Определите основные параметры профиля VPN

    $Script = '$ProfileName = ''' + $ProfileName + '''
    $ProfileNameEscaped = $ProfileName -replace ' ', '%20'

## Определение VPN ProfileXML

    $ProfileXML = ''' + $ProfileXML + '''
    
### Избежать специальных символов в профиле

    $ProfileXML = $ProfileXML -replace '<', '&lt;'
    $ProfileXML = $ProfileXML -replace '>', '&gt;'
    $ProfileXML = $ProfileXML -replace '"', '&quot;'
    
### Определите свойства моста WMI-CSP

    $nodeCSPURI = "./Vendor/MSFT/VPNv2"
    $namespaceName = "root\cimv2\mdm\dmmap"
    $className = "MDM_VPNv2_01"

### Определите SID пользователя для VPN-профиля:

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
    

### Определите сеанса WMI:

    $session = New-CimSession
    $options = New-Object Microsoft.Management.Infrastructure.Options.CimOperationOptions
    $options.SetCustomOption("PolicyPlatformContext_PrincipalContext_Type", "PolicyPlatform_UserContext", $false)
    $options.SetCustomOption("PolicyPlatformContext_PrincipalContext_Id", "$SidValue", $false)


### Обнаружение и удаление предыдущих VPN-профиля:

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
    

### Создание профиля VPN.

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

### Сохраните XML-файл профиля

    $Script | Out-File -FilePath ($env:USERPROFILE + '\desktop\VPN_Profile.ps1')
    
    $Message = "Successfully created VPN_Profile.xml and VPN_Profile.ps1 on the desktop."
    Write-Host "$Message"

## <a name="bkmk_fullscript"></a>Полный скрипт MakeProfile.ps1

Большинство примеров этот командлет Set-WmiInstance Windows PowerShell для вставки ProfileXML в новый экземпляр класса MDM_VPNv2_01 WMI. 

Тем не менее это не работает в System Center Configuration Manager, так как не удается запустить пакет в контексте конечных пользователей. Таким образом этот сценарий использует модель CIM для создания сеанса WMI в контексте пользователя, и затем создает новый экземпляр класса MDM_VPNv2_01 WMI во время этого сеанса. Этот класс WMI для настройки VPNv2 CSP используется мост WMI-CSP. Таким образом добавляя экземпляр класса, настройте CSP. 

>[!IMPORTANT]
>Мост WMI-CSP требуются права локального администратора, намеренно. Для развертывания на VPN-профили пользователей вы должны использовать SCCM или MDM.

>[!NOTE]
>Сценарий VPN_Profile.ps1 использует SID текущего пользователя для идентификации контекста пользователя. Так как не SID доступен во время сеанса удаленного рабочего стола, сценарий не работает в сеансе удаленного рабочего стола. Аналогичным образом он не работает в Hyper-V расширенного сеанса. Если вы тестируете удаленного доступа VPN на виртуальных машинах, отключите расширенного сеанса на клиентских виртуальных машин, прежде чем запустить этот сценарий.

В следующем примере сценария включает все примеры кода в предыдущих разделах. Убедитесь, что значения пример значения, которые подходят для вашей среды.
    
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

## Настройка VPN-клиент с помощью Windows PowerShell

Чтобы настроить VPNv2 CSP на клиентском компьютере с Windows 10, запустите сценарий VPN_Profile.ps1 Windows PowerShell, созданный в разделе " [Создание профиля XML](#create-the-profile-xml) ". Откройте Windows PowerShell от имени администратора; в противном случае вы получите ошибка с сообщением, _Отказано в доступе_.

После выполнения VPN_Profile.ps1 для настройки VPN-профиль, можно проверить в любое время ее успешном, выполнив следующую команду в интегрированной среды Сценариев Windows PowerShell:

    Get-WmiObject -Namespace root\cimv2\mdm\dmmap -Class MDM_VPNv2_01

**Результаты из командлета Get-WmiObject**


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

Конфигурация ProfileXML должен быть в структуру, проверки орфографии, настройки и иногда регистра. Если вы видите, что-то еще в структуре описания 1, вероятно, разметка ProfileXML содержит ошибку.

Если вам необходимо выявить неполадки разметки, проще поместить его в редактор XML, чем Устранение в интегрированной среде Сценариев Windows PowerShell. В любом случае начните с простой версию профиля и добавить компоненты назад по очереди до проблема повторится.

## <a name="vpn-deploy-client-sccm"></a>Настройка VPN-клиент с помощью System Center Configuration Manager

В System Center Configuration Manager, вы можете развернуть профили VPN с помощью узел ProfileXML CSP, так же, как и в Windows PowerShell. Здесь используется сценарий VPN_Profile.ps1 Windows PowerShell, созданный в разделе, [Создайте файлы конфигурации ProfileXML](#bkmk_ProfileXML).

Чтобы использовать System Center Configuration Manager для развертывания удаленного доступа всегда в профиль VPN для клиентских компьютеров с Windows 10, необходимо запустить, создав группу компьютеров или пользователей, которым необходимо развернуть профиль. В этом случае создайте группу пользователей для развертывания сценарий настройки.

### Создание группы пользователей

1.  В консоли Configuration Manager откройте ресурсы и Compliance\\User коллекции.

2.  На **Домашняя** ленте в группе **Создать** щелкните **Создать коллекцию пользователя**.

3.  На странице "Общие" выполните следующие действия:

    А. В поле **имени**введите **Пользователей VPN**.

    Б. Нажмите кнопку **Обзор**, щелкните **Всех пользователей** и нажмите кнопку **ОК**.

    в. Нажмите кнопку **Далее**.

4.  На странице "правила членства" выполните следующие действия:

    А.  **Правила членства**нажмите кнопку **Добавить правило**, а затем **Прямое правило**. В этом примере отдельным пользователям добавляемый к коллекции пользователя. Тем не менее можно использовать для добавления пользователей в этой коллекции динамически для развертывания более масштабные правила запроса.

    Б.  На странице **приветствия** нажмите кнопку " **Далее**".

    в.  Во время поиска ресурсов страницы, **значение**введите имя пользователя, которого вы хотите добавить. Имя ресурса включает в себя пользователя домена. Чтобы включить результаты в зависимости от частичное соответствие, вставьте **%** символов на концах вашего условие поиска. Например, чтобы найти все пользователи, содержащей строку «Лори», введите **% Лори %**. Нажмите кнопку **Далее**.

    г.  На странице "Выбор ресурсов" выберите пользователей, которые вы хотите добавить в группу и нажмите кнопку **Далее**.

    д.  На странице "Сводка" нажмите кнопку " **Далее**".

    е.  На странице Завершение щелкните **Закрыть**.

6.  Вернитесь на странице правила членства мастере создания коллекции пользователей нажмите кнопку " **Далее**".

7.  На странице "Сводка" нажмите кнопку " **Далее**".

8.  На странице Завершение щелкните **Закрыть**.

После создания группы пользователей для получения профиля VPN, можно создать пакет и программы для развертывания конфигурации сценарий Windows PowerShell, созданный в разделе, [Создайте файлы конфигурации ProfileXML](#bkmk_ProfileXML).

### Создание пакета, содержащего сценарий настройки ProfileXML

1.  Узел сценарий VPN_Profile.ps1 на общем сетевом ресурсе, который можно получить доступ к учетной записи компьютера сервера сайта.

2.  В консоли Configuration Manager откройте **Management\\Packages Library\\Application программного обеспечения**.

3.  На **Домашняя** ленте в группе **Создать** щелкните **Создать пакет** для запуска мастера программы и создать пакет.

4.  На странице "пакет" выполните следующие действия:

    А. В поле **имени**введите **Windows 10 всегда на VPN-профиль**.

    Б. Установите флажок **Этот пакет содержит исходные файлы** и нажмите кнопку **Обзор**.

    в. В диалоговом окне задайте исходной папки нажмите кнопку **Обзор**, выберите общую папку файл, содержащий VPN_Profile.ps1 и нажмите кнопку **ОК**.<p>Убедитесь, что выбран сетевого пути, не локальный путь. Другими словами путь должен быть что-то вроде *\\fileserver\\vpnscript*, не *c:\\vpnscript*.

1.  Нажмите кнопку **Далее**.

2.  На странице тип программы нажмите кнопку " **Далее**".

3.  На странице "Стандартная программа" выполните следующие действия:

    А.  В поле **имени**введите **Сценарий профиля VPN**.

    Б.  В **командной строке**введите **обходить PowerShell.exe - ExecutionPolicy - файла «VPN_Profile.ps1»**.

    в.  В **режиме выполнения**выберите **запускать с правами администратора**.

    г.  Нажмите кнопку **Далее**.

4.  На странице "требования" выполните следующие действия:

    А.  Выберите **эту программу можно запустить только на указанном платформах**.

    Б.  Установите флажки **всех Windows 10 (32-разрядная версия)** и **все Windows 10 (64-разрядная версия)** .

    в.  **Оценка места на диске**введите значение **1**.

    г.  В **Максимальное время выполнения (в минутах)** введите **15**.

    д.  Нажмите кнопку **Далее**.

5.  На странице "Сводка" нажмите кнопку " **Далее**".

6.  На странице Завершение щелкните **Закрыть**.

С помощью пакета и программы, созданной необходимо развернуть ее в группу **Пользователей VPN** .

### Развертывание сценария настройки ProfileXML

1.  В консоли Configuration Manager откройте Management\\Packages Library\\Application программного обеспечения.

2.  В **пакеты**выберите **Windows 10 всегда на VPN-профиль**.

3.  На вкладке « **программы** » в нижней части области сведений щелкните правой кнопкой мыши **Сценарий профиля VPN**, щелкните **Свойства**и выполните следующие действия:

    А.  На вкладке " **Дополнительно** " в списке, **Когда к компьютеру назначается этой программы**щелкните **один раз для каждого пользователя, который входит в систему**.

    Б.  Нажмите кнопку **ОК**.

4.  Щелкните правой кнопкой мыши **Сценарий профиля VPN** и щелкните **Развертывание** , чтобы запустить мастер развертывания программного обеспечения.

5.  На странице "Общие" выполните следующие действия:

    А.  Рядом с **коллекцию**нажмите кнопку " **Обзор**".

    Б.  В списке **Типов коллекций** (верхнем левом углу) щелкните **Коллекции пользователя**.

    в.  Выберите **Пользователей VPN**и нажмите кнопку **ОК**.

    г.  Нажмите кнопку **Далее**.

6.  На странице "содержимое" выполните следующие действия:

    А.  Нажмите кнопку **Добавить**и выберите **Точку распространения**.

    Б.  В **точки распространения доступны**выберите точки распространения, к которым вы хотите распространять сценарий настройки ProfileXML и нажмите кнопку **ОК**.

    в.  Нажмите кнопку **Далее**.

7.  На странице "Параметры развертывания" нажмите кнопку " **Далее**".

8.  На странице "Планирование" выполните следующие действия:

    А.  Щелкните **New** , чтобы открыть диалоговое окно Расписание назначений.

    Б.  Нажмите кнопку **назначить сразу после этого события**и нажмите кнопку **ОК**.

    в.  Нажмите кнопку **Далее**.

9.  На странице "взаимодействие с пользователем" выполните следующие действия:

    1.  Установите флажок **«Установка программ»** .

    2.  Щелкните **Сводка**.

10. На странице "Сводка" нажмите кнопку " **Далее**".

11. На странице Завершение щелкните **Закрыть**.

С помощью сценария конфигурации ProfileXML развертывания вход на клиентском компьютере с Windows 10 с помощью учетной записи пользователя, выбранные при построении коллекции пользователя. Проверка конфигурации VPN-клиента.

>[!NOTE]
>Сценарий VPN_Profile.ps1 не работает в сеансе удаленного рабочего стола. Аналогичным образом он не работает в Hyper-V расширенного сеанса. Если вы тестируете удаленного доступа VPN на виртуальных машинах, отключите расширенного сеанса на клиентских виртуальных машин перед продолжением.

### Проверка конфигурации VPN-клиента

1.  На панели управления **System\\Security**, установите для **Configuration Manager**. 

2.  В диалоговом окне Свойства Configuration Manager, на вкладке " **действия** " выполните следующие действия:

    А.  Щелкните **& загрузка компьютера политики цикл оценки**, щелкните **Выполнить**и нажмите кнопку **ОК**.

    Б.  Нажмите кнопку **Загрузка политики пользователя & цикл оценки**, щелкните **Выполнить**и нажмите кнопку **ОК**.

    в.  Нажмите кнопку **ОК**.

3.  Закройте панели управления.

Вы должны увидеть вскоре нового профиля VPN.

## Настройка VPN-клиент с помощью Intune

Использовать Intune для развертывания Windows 10 удаленного доступа VPN профилей, можно настроить узел ProfileXML CSP с помощью VPN-профиль, который вы создали в разделе, [Создайте файлы конфигурации ProfileXML](#bkmk_ProfileXML)или можно использовать базовый примера EAP XML ниже.

>[!NOTE]
>Теперь Intune использует Azure AD группы. Если Azure AD Connect синхронизировать группу пользователей VPN из локальной к Azure AD, а пользователям назначены группе пользователей VPN, вы готовы для продолжения.

Создание политики конфигурации VPN устройства для настройки клиентских компьютеров Windows 10 для всех пользователей, добавляемых в группу. Так как шаблон Intune предоставляет параметры VPN, копировать только \<EapHostConfig> \</EapHostConfig> часть файла VPN_ProfileXML. 


### Создание политики конфигурации VPN

1.  Войдите на [портал Azure](https://portal.azure.com/).

2.  Последовательно выберите пункты **Intune** > **конфигурацию устройства** > **профилей**.

3.  Выберите **Создать профиль** для запуска мастера создать профиль.

4.  Введите **имя** для профиля VPN и (при необходимости) описание.

5.   В разделе **платформы**выберите **Windows 10 или более поздней версии**и выберите из раскрывающегося списка тип профиля **VPN** .

     >[!TIP]
     >Если вы создаете пользовательский profileXML VPN, см. в разделе [Применение ProfileXML с помощью Intune](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-profile-options#apply-profilexml-using-intune) инструкции.

6. На вкладке " **Base VPN** проверить или задайте следующие параметры:

    - **Имя подключения:** Введите имя для подключения VPN, как она отображается на клиентском компьютере, на вкладке " **VPN** " в разделе **параметров**, например, _Contoso AutoVPN_.  
    
    - **Серверов:** Добавьте один или несколько VPN-серверов, нажав кнопку **Добавить.**
    
    - **Описание** и **IP-адрес или полное доменное имя:** введите описание и IP-адрес или полное доменное имя VPN-сервера. Эти значения необходимо согласовать с именем субъекта сертификата проверки подлинности VPN-сервер. 
    
    - **Сервера по умолчанию:** Если VPN-сервер по умолчанию, задайте значение **True**. Это позволяет этого сервера в качестве сервера по умолчанию, устройства используют для подключения. 
    
    - **Тип подключения:** Установите **IKEv2**.  
    
    - **Постоянно включенной:** Для **включения** для подключения к VPN автоматически при входе в систему и оставаться на связи, пока пользователь вручную не разорвет установлено.
    
    - **Запомнить учетные данные при каждом входе в систему**: логическое значение (true или false) для кэширования учетных данных. Если задано значение true, учетные данные кэшируются, когда это возможно.

7.  Скопируйте следующую строку XML-ФАЙЛ в текстовом редакторе:<p>
 
    [!INCLUDE [important-lower-case-true-include](../../../includes/important-lower-case-true-include.md)]
    <p>
    
    ```XML
    <EapHostConfig xmlns="https://www.microsoft.com/provisioning/EapHostConfig"><EapMethod><Type xmlns="https://www.microsoft.com/provisioning/EapCommon">25</Type><VendorId xmlns="https://www.microsoft.com/provisioning/EapCommon">0</VendorId><VendorType xmlns="https://www.microsoft.com/provisioning/EapCommon">0</VendorType><AuthorId xmlns="https://www.microsoft.com/provisioning/EapCommon">0</AuthorId></EapMethod><Config xmlns="https://www.microsoft.com/provisioning/EapHostConfig"><Eap xmlns="https://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1"><Type>25</Type><EapType xmlns="https://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV1"><ServerValidation><DisableUserPromptForServerValidation>true</DisableUserPromptForServerValidation><ServerNames>NPS.contoso.com</ServerNames><TrustedRootCA>5a 89 fe cb 5b 49 a7 0b 1a 52 63 b7 35 ee d7 1c c2 68 be 4b </TrustedRootCA></ServerValidation><FastReconnect>true</FastReconnect><InnerEapOptional>false</InnerEapOptional><Eap xmlns="https://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1"><Type>13</Type><EapType xmlns="https://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1"><CredentialsSource><CertificateStore><SimpleCertSelection>true</SimpleCertSelection></CertificateStore></CredentialsSource><ServerValidation><DisableUserPromptForServerValidation>true</DisableUserPromptForServerValidation><ServerNames>NPS.contoso.com</ServerNames><TrustedRootCA>5a 89 fe cb 5b 49 a7 0b 1a 52 63 b7 35 ee d7 1c c2 68 be 4b </TrustedRootCA></ServerValidation><DifferentUsername>false</DifferentUsername><PerformServerValidation xmlns="https://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">true</PerformServerValidation><AcceptServerName xmlns="https://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">true</AcceptServerName></EapType></Eap><EnableQuarantineChecks>false</EnableQuarantineChecks><RequireCryptoBinding>false</RequireCryptoBinding><PeapExtensions><PerformServerValidation xmlns="https://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV2">true</PerformServerValidation><AcceptServerName xmlns="https://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV2">true</AcceptServerName></PeapExtensions></EapType></Eap></Config></EapHostConfig>
    ```

8.  Замените **\<TrustedRootCA>5a 89 fe cb 5b 49 ответ 7 0b 1a 52 63 b7 35 ee d7 1c c2 68 быть 4b<\/TrustedRootCA>** в примере с отпечаток сертификата из вашей локальной корневых центров сертификации в одном из разделов.
  
    >[!Important]
    >Не используйте отпечаток пример \<TrustedRootCA>\</TrustedRootCA> ниже в разделе.  TrustedRootCA должен быть отпечаток сертификата локального корневого центра сертификации, выпустившего сертификат проверки подлинности сервера для службы RRAS и NPS серверов. **Это не должно быть облачных корневой сертификат, ни промежуточных отпечаток сертификата выдающего центра сертификации**.

10. Замените **\<ServerNames>NPS.contoso.com\</ServerNames>** в примере XML-ФАЙЛ с полным доменным ИМЕНЕМ NPS присоединенный к домену, где будет выполнена проверка подлинности. 

11. Скопируйте пересмотренные строку XML-ФАЙЛ и вставьте в это поле **EAP Xml** на вкладке "Base VPN" и нажмите кнопку **ОК**.<p>Политики всегда на устройстве конфигурация VPN с помощью EAP создается в Intune.


### Синхронизация политики конфигурации VPN с помощью Intune

Чтобы проверить политику конфигурации, вход на клиентском компьютере Windows10 имени пользователя, который вы добавили в группу **Всегда на пользователей VPN** и синхронизировать с помощью Intune.

1.  В меню "Пуск" нажмите кнопку " **Параметры**".

2.  В параметрах нажмите кнопку **учетные записи**, а затем **доступ к рабочей или учебной учетной записи**.

3.  Выберите профиль MDM и нажмите кнопку **сведения**.

4.  Нажмите кнопку **синхронизации** для принудительного оценку политики Intune и извлечения.

5.  Закройте параметры. После синхронизации см. доступные профиля VPN на компьютере.

## Дальнейшие действия
Вы закончили развертывание VPN.  Для других функций, которые можно настроить см. в следующей таблице:

|Если вы хотите …  |Затем см.  |
|---------|---------|
|Настройка условного доступа для VPN    |[Шаг 7. (Необязательно) Настройка условного доступа для VPN-подключения с помощью Azure AD](../../ad-ca-vpn-connectivity-windows10.md): на этом этапе можно настроить параметры как санкционированный доступ пользователей VPN свои ресурсы с помощью [условным доступом Azure Active Directory (Azure AD)](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). С помощью условного доступа Azure AD для подключения к виртуальной частной сети (VPN) чтобы защитить VPN-подключений. Условный доступ — это модуль оценки на основе политик, который позволяет создавать правила доступа для любого приложения, подключенного к Azure Active Directory (Azure AD).         |
|Дополнительные сведения о расширенных возможностях VPN  |[Дополнительные параметры VPN](always-on-vpn-adv-options.md#advanced-vpn-features): на этой странице приведены рекомендации по Включение фильтры трафика VPN, как настроить автоматическое VPN-подключений с помощью приложений-триггеров и настройка сервера политики сети, чтобы разрешить VPN-подключения только от клиентов, использующих сертификаты, выданные Azure РЕКЛАМА.        |


---
