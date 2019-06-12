---
title: Настроить устройство VPN-туннеля в Windows 10
description: Сведения о создании VPN-туннель устройства в Windows 10.
ms.prod: windows-server-threshold
ms.date: 11/05/2018
ms.technology: networking-ras
ms.topic: article
ms.assetid: 158b7a62-2c52-448b-9467-c00d5018f65b
ms.author: pashort
author: shortpatti
ms.localizationpriority: medium
ms.openlocfilehash: 989216f90e78689b464240cff957bab1d9c1229b
ms.sourcegitcommit: 0948a1abff1c1be506216eeb51ffc6f752a9fe7e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2019
ms.locfileid: "66749569"
---
# <a name="configure-vpn-device-tunnels-in-windows-10"></a>Настройка VPN-туннели устройства в Windows 10

>Относится к: Windows 10 версии 1709

AlwaysOn VPN дает возможность создать профиль VPN, выделенный для устройства или компьютера. Всегда на VPN-подключения включают два типа туннелей. 

- _Туннель устройства_ подключается к указанным серверам VPN перед пользователям войти на устройство. Сценарии подключения перед входом и целей управления устройства используют туннель устройства.

- _Туннель пользователя_ подключается только после входа пользователя в систему на устройстве. Туннель пользователя позволяет пользователям получить доступ к ресурсам организации через VPN-серверов.

В отличие от _туннель пользователя_, который подключает только после входа пользователя в систему на устройстве или компьютере, _туннель устройства_ позволяет VPN, чтобы установить подключение, прежде чем он войдет в систему. Оба _туннель устройства_ и _туннель пользователя_ работают независимо друг от друга с помощью своих профилей VPN, можно подключить в то же время и можно использовать разные методы проверки подлинности и другие параметры конфигурации VPN по мере необходимости. Туннель пользователя поддерживает SSTP и IKEv2, а туннель устройство поддерживает IKEv2 только с не поддерживаются для резервной проверки подлинности SSTP.

Туннель пользователя поддерживается на присоединенных к домену, присоединенного к домену не входящей в домен (в рабочей группе) или Azure AD — объединить устройств, чтобы разрешить как для корпоративного и BYOD. Он доступен во всех выпусках Windows, и функции платформы доступны третьим лицам посредством поддержки подключаемого модуля VPN универсальной платформы Windows.

Туннель устройства можно настроить только на устройствах, присоединенных к домену под управлением Windows 10 Корпоративная и образования версии 1709 или более поздней версии. Элемент управления стороннего туннеля устройства не поддерживается.


## <a name="device-tunnel-requirements-and-features"></a>Требования к устройствам туннеля и компоненты
Необходимо включить проверку подлинности сертификата компьютера для VPN-подключений и определить корневой центр сертификации для проверки подлинности входящих подключений VPN. 

```PowerShell
$VPNRootCertAuthority = “Common Name of trusted root certification authority”
$RootCACert = (Get-ChildItem -Path cert:LocalMachine\root | Where-Object {$_.Subject -Like “*$VPNRootCertAuthority*” })
Set-VpnAuthProtocol -UserAuthProtocolAccepted Certificate, EAP -RootCertificateNameToAccept $RootCACert -PassThru
```

![Устройство туннелирования функции и требования](../../media/device-tunnel-feature-and-requirements.png)

## <a name="vpn-device-tunnel-configuration"></a>Конфигурация туннеля VPN-устройств

Пример профиля, следующий XML предоставляет полезные рекомендации для сценариев, где только клиент инициирована переносит требуются через туннель устройства.  Фильтры трафика используются для ограничения устройства туннель к только трафик управления.  Эта конфигурация подходит для обновления Windows, типичный групповой политики (GP) и сценариев обновления System Center Configuration Manager (SCCM), а также VPN-подключение для первого входа в систему без кэшированные учетные данные или сценариев для сброса пароля. 

Для случаев, инициированного сервером Push-уведомлений, как удаленное управление Windows (WinRM), удаленного запуска Gpupdate.exe и удаленный SCCM обновления сценариев – необходимо разрешить входящий трафик на устройство туннель, поэтому нельзя использовать фильтры трафика.  Если в профиле устройства туннель включить фильтры трафика, туннель устройство отклоняет входящий трафик.  Это ограничение будет удален в будущих выпусках.


### <a name="sample-vpn-profilexml"></a>Пример VPN profileXML

Ниже приведен пример profileXML VPN.

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

В зависимости от потребностей каждого конкретного развертывания сценария, — еще одна функция VPN, можно настроить с помощью туннеля устройства [доверенные определение сетевого](https://social.technet.microsoft.com/wiki/contents/articles/38546.new-features-for-vpn-in-windows-10-and-windows-server-2016.aspx#Trusted_Network_Detection).

```
 <!-- inside/outside detection -->
  <TrustedNetworkDetection>corp.contoso.com</TrustedNetworkDetection>
```

## <a name="deployment-and-testing"></a>Развертывание и тестирование

Туннели устройства можно настроить с помощью сценариев Windows PowerShell и с помощью моста инструментария управления Windows (WMI). Всегда на VPN-туннеля устройства должен быть настроен в контексте **LOCAL SYSTEM** учетной записи. Чтобы добиться этого, он будет необходимо использовать [PsExec](https://docs.microsoft.com/sysinternals/downloads/psexec), используя один из [PsTools](https://docs.microsoft.com/sysinternals/downloads/pstools) состава [Sysinternals](https://docs.microsoft.com/sysinternals/) набор служебных программ.

Инструкции по развертыванию каждого устройства `(.\Device)` и каждого пользователя `(.\User)` профилировать, см. в разделе [PowerShell с помощью сценариев с поставщиком WMI моста](https://docs.microsoft.com/windows/client-management/mdm/using-powershell-scripting-with-the-wmi-bridge-provider).

Выполните следующую команду Windows PowerShell, чтобы убедиться, что вы успешно развернули профиль устройства:

  ```powershell
  Get-VpnConnection -AllUserConnection
  ```

Вывод списка устройства\-широкий профили VPN, развернутых на устройстве.

### <a name="example-windows-powershell-script"></a>Пример сценария PowerShell для Windows

При создании собственного скрипта для создания профиля можно использовать следующий сценарий Windows PowerShell.

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

## <a name="additional-resources"></a>Дополнительные ресурсы

Ниже приведены дополнительные ресурсы, помогающие при развертывании VPN.

### <a name="vpn-client-configuration-resources"></a>Ресурсы конфигурации клиента VPN

Ниже приведены ресурсы настройки клиента VPN.

- [Как создание профилей VPN в System Center Configuration Manager](https://docs.microsoft.com/sccm/protect/deploy-use/create-vpn-profiles)
- [Настройка клиента Windows 10 AlwaysOn VPN-подключений](always-on-vpn/deploy/vpn-deploy-client-vpn-connections.md)
- [Параметры для профиля VPN](https://docs.microsoft.com/windows/access-protection/vpn/vpn-profile-options)

### <a name="remote-access-server-gateway-resources"></a>Удаленные ресурсы сервера Access Gateway

Ниже приведены ресурсы шлюза сервера удаленного доступа (RAS).

- [Настройка RRAS с сертификатом проверки подлинности компьютера](https://technet.microsoft.com/library/dd458982.aspx)
- [Устранение неполадок VPN-подключения IKEv2](https://technet.microsoft.com/library/dd941612.aspx)
- [Настройка удаленного доступа на основе IKEv2](https://technet.microsoft.com/library/ff687731.aspx)

>[!IMPORTANT]
>Используя туннель устройства шлюза Microsoft RAS, необходимо настроить сервер RRAS для поддержки проверки подлинности сертификата компьютера IKEv2, включив **разрешить проверку подлинности сертификата компьютера для IKEv2** метод проверки подлинности, как описано [здесь](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee922682%28v=ws.10%29). Когда этот параметр включен, настоятельно рекомендуется, **набора VpnAuthProtocol** командлет PowerShell вместе с **RootCertificateNameToAccept** используется необязательный параметр, чтобы убедиться, что Подключения IKEv2 в RRAS разрешены только для клиентских сертификатов VPN, привязанные к явно определенной внутренней и закрытого корневого центра сертификации. Кроме того **доверенные корневые центры сертификации** хранилище на сервере RRAS исправляются, чтобы убедиться, что он не содержит общедоступные центры сертификации рассматривался [здесь](https://blogs.technet.microsoft.com/rrasblog/2009/06/10/what-type-of-certificate-to-install-on-the-vpn-server/). Аналогичные методы могут также необходимо учитывать для других VPN-шлюзов.

