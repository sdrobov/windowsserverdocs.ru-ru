---
title: Настройка устройства туннеля VPN в Windows 10
description: Узнайте, как создать туннель устройства VPN в Windows 10.
ms.prod: windows-server-threshold
ms.date: 11/05/2018
ms.technology: networking-ras
ms.topic: article
ms.assetid: 158b7a62-2c52-448b-9467-c00d5018f65b
ms.author: pashort
author: shortpatti
ms.localizationpriority: medium
ms.openlocfilehash: 005721873ad3a0df942bc9e23eba13728965ccba
ms.sourcegitcommit: 4893d79345cea85db427224bb106fc1bf88ffdbc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2018
ms.locfileid: "6067481"
---
# Настройка устройства Туннели VPN в Windows 10

>Область применения: Windows 10 версии 1709

VPN дает возможность создания специальной профиль VPN для устройства или компьютера. Подключения VPN включают два типа туннелей: 

- _Туннеля устройство_ подключается к указанной VPN-серверов перед пользователям входить на устройстве. Сценарии подключения до входа в систему и устройство управления целей использования туннеля устройства.

- _Пользователь туннеля_ подключается только после входа пользователя на этом устройстве. Туннеля пользователя позволяет пользователям получать доступ к ресурсам организации через VPN-серверов.

В отличие от _туннеля пользователя_, который подключается только после входа пользователя в систему на устройстве или компьютере, _туннеля устройства_ позволяет VPN для установления подключения, прежде чем пользователь входит в систему. _Туннеля устройства_ и _пользователя туннеля_ работать независимо друг от друга, с помощью профилей VPN, можно подключить одновременно и могут использовать различные методы проверки подлинности и другие параметры конфигурации VPN соответствующим образом. Пользователь туннеля поддерживает SSTP и IKEv2, а туннеля устройства поддерживает IKEv2 только с поддержка SSTP резервный.

Пользователь туннеля поддерживается на присоединенный к домену, неподключенные к домену (рабочей группы) или Azure AD — устройств для корпоративных и BYOD-сценариев. Он доступен во всех выпусках Windows, и возможностей платформы доступны третьим лицам через поддержка подключаемого модуля UWP VPN.

Туннеля устройства можно настроить только на присоединенный к домену устройства с Windows 10 Корпоративная или для образовательных учреждений версии 1709 или более поздней версии. Не поддерживается для элемента управления стороннего туннеля устройства.


## Требования к туннеля устройства и компоненты
Необходимо включить проверку подлинности сертификата компьютера для VPN-подключений и определение корневых центров сертификации для проверки подлинности входящих подключений VPN. 

```PowerShell
$VPNRootCertAuthority = “Common Name of trusted root certification authority”
$RootCACert = (Get-ChildItem -Path cert:LocalMachine\root | Where-Object {$_.Subject -Like “*$VPNRootCertAuthority*” })
Set-VpnAuthProtocol -UserAuthProtocolAccepted Certificate, EAP -RootCertificateNameToAccept $RootCACert -PassThru
```

![Компоненты туннеля устройства и требования](../../media/device-tunnel-feature-and-requirements.png)

## Настройка устройства туннеля VPN

Пример профиля, предоставляемых хорошо инструкции для сценариев, где только клиент инициировал сдвигает XML ниже являются обязательными через туннель устройства.  Фильтры трафика используются для ограничения туннеля устройства только трафик управления.  Такая конфигурация лучше всего подойдет для центра обновления Windows, обычно групповой политики (GP) и сценариев обновления System Center Configuration Manager (SCCM), а также подключения к VPN для первого входа в систему без кэшированные учетные данные или сценариев сброса пароля. 

Для случаев, инициированные сервера Push-уведомлений, как удаленного управления Windows (WinRM), удаленный GPUpdate и дистанционные сценарии обновления SCCM — должны разрешать входящий трафик на туннеля устройства, поэтому нельзя использовать фильтры трафика.  Если в профиле туннеля устройства включения фильтры трафика туннеля устройства запрещает входящий трафик.  Это ограничение будет удален в будущих выпусках.


### Пример VPN profileXML

Ниже приведен пример VPN profileXML.

``` xml
<VPNProfile>  
  <NativeProfile>  
<Servers>vpn.contoso.com</Servers>  
<NativeProtocolType>IKEv2</NativeProtocolType>  
<Authentication>  
  <MachineMethod>Certificate</MachineMethod>  
</Authentication>  
<RoutingPolicyType>SplitTunnel</RoutingPolicyType>  
 <!-- disable the addition of a class based route for the assigned IP address on the VPN interface -->
<DisableClassBasedDefaultRoute>true</DisableClassBasedDefaultRoute>  
  </NativeProfile> 
  <!-- use host routes(/32) to prevent routing conflicts -->  
  <Route>  
<Address>10.10.0.2</Address>  
<PrefixSize>32</PrefixSize>  
  </Route>  
  <Route>  
<Address>10.10.0.3</Address>  
<PrefixSize>32</PrefixSize>  
  </Route>  
<!-- traffic filters for the routes specified above so that only this traffic can go over the device tunnel --> 
  <TrafficFilter>  
<RemoteAddressRanges>10.10.0.2, 10.10.0.3</RemoteAddressRanges>  
  </TrafficFilter>
<!-- need to specify always on = true --> 
  <AlwaysOn>true</AlwaysOn> 
<!-- new node to specify that this is a device tunnel -->  
 <DeviceTunnel>true</DeviceTunnel>
<!--new node to register client IP address in DNS to enable manage out -->
<RegisterDNS>true</RegisterDNS>
</VPNProfile>
```

В зависимости от потребностей каждого конкретного развертывания сценария еще одна функция VPN, который можно настроить с помощью туннеля устройства — это [Надежная обнаружение сети](https://social.technet.microsoft.com/wiki/contents/articles/38546.new-features-for-vpn-in-windows-10-and-windows-server-2016.aspx#Trusted_Network_Detection).

```
 <!-- inside/outside detection --> 
  <TrustedNetworkDetection>corp.contoso.com</TrustedNetworkDetection> 
```

## Развертывание и тестирование

Туннели устройства можно настроить с помощью сценарий Windows PowerShell и инструментария управления Windows \(WMI\) мостом. Туннеля VPN устройства должно быть настроено в контексте учетной записи **Локальной системы** . Чтобы добиться этого, будет необходимо использовать [PsExec](https://docs.microsoft.com/sysinternals/downloads/psexec), один из [PsTools](https://docs.microsoft.com/sysinternals/downloads/pstools) , включенные в пакет [Sysinternals](https://docs.microsoft.com/sysinternals/) suite служебных программ.

Инструкции о том, как развернуть на устройство `(.\Device)` или каждого пользователя `(.\User)` профиля, см. в разделе [сценариев с помощью PowerShell с WMI Bridge Provider](https://docs.microsoft.com/windows/client-management/mdm/using-powershell-scripting-with-the-wmi-bridge-provider). 

Выполните следующую команду Windows PowerShell, чтобы убедиться, что успешно развернуты профиль устройства:

    `Get-VpnConnection -AllUserConnection`

В выходных данных отображается список профилей VPN device\ уровне, которые развертываются на устройстве.


### Пример сценария Windows PowerShell

Следующий сценарий Windows PowerShell можно использовать для помощи в создании собственных сценарий для создания профиля.

```PowerShell
Param(
[string]$xmlFilePath,
[string]$ProfileName
)

$a = Test-Path $xmlFilePath
echo $a

$ProfileXML = Get-Content $xmlFilePath

echo $XML

$ProfileNameEscaped = $ProfileName -replace ' ', '%20'

$Version = 201606090004

$ProfileXML = $ProfileXML -replace '<', '&lt;'
$ProfileXML = $ProfileXML -replace '>', '&gt;'
$ProfileXML = $ProfileXML -replace '"', '&quot;'

$nodeCSPURI = './Vendor/MSFT/VPNv2'
$namespaceName = "root\cimv2\mdm\dmmap"
$className = "MDM_VPNv2_01"

$session = New-CimSession

try
{
$newInstance = New-Object Microsoft.Management.Infrastructure.CimInstance $className, $namespaceName
$property = [Microsoft.Management.Infrastructure.CimProperty]::Create("ParentID", "$nodeCSPURI", 'String', 'Key')
$newInstance.CimInstanceProperties.Add($property)
$property = [Microsoft.Management.Infrastructure.CimProperty]::Create("InstanceID", "$ProfileNameEscaped", 'String', 'Key')
$newInstance.CimInstanceProperties.Add($property)
$property = [Microsoft.Management.Infrastructure.CimProperty]::Create("ProfileXML", "$ProfileXML", 'String', 'Property')
$newInstance.CimInstanceProperties.Add($property)

$session.CreateInstance($namespaceName, $newInstance)
$Message = "Created $ProfileName profile."
Write-Host "$Message"
}
catch [Exception]
{
$Message = "Unable to create $ProfileName profile: $_"
Write-Host "$Message"
exit
}
$Message = "Complete."
Write-Host "$Message"
```

## Дополнительные ресурсы

Ниже приведены дополнительные ресурсы для помощи в развертывании VPN.

### Ресурсы конфигурации клиент VPN

Ниже перечислены ресурсы конфигурации клиент VPN.

- [Как создать VPN-профили в System Center Configuration Manager](https://docs.microsoft.com/sccm/protect/deploy-use/create-vpn-profiles)
- [Настройка подключений постоянно подключенного VPN-профиля клиента Windows 10](always-on-vpn/deploy/vpn-deploy-client-vpn-connections.md)
- [Параметры профиля VPN](https://docs.microsoft.com/windows/access-protection/vpn/vpn-profile-options)

### Удаленный сервер доступа \(RAS\) ресурсы шлюза

Ниже приведены ресурсы шлюз RAS-сервера.

- [Настройка RRAS с сертификатом проверки подлинности компьютера](https://technet.microsoft.com/library/dd458982.aspx)
- [Устранение неполадок VPN-подключений IKEv2](https://technet.microsoft.com/library/dd941612.aspx)
- [Настройка удаленного доступа по протоколу IKEv2](https://technet.microsoft.com/library/ff687731.aspx)

>[!IMPORTANT]
>Если вы используете туннеля устройства шлюза RAS-сервера Microsoft, необходимо настроить сервер RRAS для поддержки проверки подлинности сертификата компьютера IKEv2, включив метод проверки подлинности **сертификата проверки подлинности компьютера разрешить для IKEv2** , как описано [здесь](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee922682%28v=ws.10%29). Когда этот параметр включен, настоятельно рекомендуется командлета PowerShell **Набор VpnAuthProtocol** вместе с необязательный параметр **RootCertificateNameToAccept** , это позволяет гарантировать, что подключений RRAS IKEv2 допускаются только для VPN-клиент сертификаты, цепочка к явно заданных внутренних и закрытых корневых центров сертификации. Кроме того чтобы убедиться, что она не содержит открытых центров сертификации как описанных [здесь](https://blogs.technet.microsoft.com/rrasblog/2009/06/10/what-type-of-certificate-to-install-on-the-vpn-server/)исправляются хранилище **Доверенных корневых центров сертификации** на сервере RRAS. Похожие методы также может потребоваться применять другие шлюзы VPN.

---
