---
title: Производительность шлюза Windows Server 2019 г.
description: ''
manager: dougkim
ms.prod: windows-server-threshold
ms.technology: networking-hv-switch
ms.topic: get-started-article
ms.assetid: ''
ms.author: pashort
author: shortpatti
ms.date: 08/22/2018
ms.openlocfilehash: a6530b29ce7ffb0d18e0266e70cb2ca45188915c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59845635"
---
# <a name="windows-server-2019-gateway-performance"></a>Производительность шлюза Windows Server 2019 г.

>Относится к: Windows Server


В Windows Server 2016 одной из задач клиента был неспособности шлюз SDN для удовлетворения требований к пропускной способности современных сетей. Пропускная способность сети туннелей IPsec и GRE было ограничений, связанных с пропускная способность одного соединения для подключения IPsec, около 300 Мбит/с, а также для подключения GRE, около 2,5 Гбит/с.

Мы значительно улучшили в Windows Server 2019, с номерами, возросшим 1,8 Гбит/с и 15 Гбит/с для подключений IPsec и GRE, соответственно. Добавьте к этому, значительное сокращение в циклах ЦП / в байте, тем самым обеспечивая сверхнизкие высокопроизводительные пропускной способности с гораздо меньше загрузкой ЦП.

## <a name="enable-high-performance-with-gateways-in-windows-server-2019"></a>Высокая производительность с помощью шлюзов в Windows Server 2019

Для **подключений GRE**, как только вы развертывания и обновления для Windows Server 2019 основана на виртуальных машинах шлюза, вы должны увидеть автоматически повышения производительности. Участвуют никакие ручные действия.

Для **подключений IPsec**, по умолчанию при создании соединения для виртуальных сетей, вы получаете номера пути и производительность данных Windows Server 2016. Чтобы включить путь к данным Windows Server 2019, сделайте следующее:

   1. На шлюз SDN виртуальной Машины, перейдите в каталог **служб** консоли (services.msc).
   2. Найдите службу с именем **службу шлюза Azure**и установите тип запуска **автоматического**.
   3. Перезапустите шлюз виртуальной Машины.
      Активные подключения на этом отработки отказа шлюза избыточных шлюз виртуальной Машины.
   4. Повторите предыдущие шаги для остальных виртуальных машинах шлюза.

>[!TIP]
>Для лучшей производительности, убедитесь, что cipherTransformationConstant и authenticationTransformConstant в параметрах быстрого режима использования подключения IPsec **GCMAES256** шифров.
>
>Для достижения максимальной производительности оборудования узла шлюза должен поддерживать AES-NI и наборы инструкций PCLMULQDQ ЦП. Они доступны на любой Westmere (32nm) и более поздних версий ЦП Intel за исключением для моделей, где AES-NI отключена. Можно просмотреть в документации изготовителя оборудования, поддерживает ли ЦП AES-NI и ЦП PCLMULQDQ инструкция задает.

Ниже приведен пример REST соединения IPsec с алгоритмами оптимальной безопасности.

```PowerShell
# NOTE: The virtual gateway must be created before creating the IPsec connection. More details here.
# Create a new object for Tenant Network IPsec Connection  
$nwConnectionProperties = New-Object Microsoft.Windows.NetworkController.NetworkConnectionProperties   

# Update the common object properties  
$nwConnectionProperties.ConnectionType = "IPSec"   
$nwConnectionProperties.OutboundKiloBitsPerSecond = 2000000   
$nwConnectionProperties.InboundKiloBitsPerSecond = 2000000  

# Update specific properties depending on the Connection Type  
$nwConnectionProperties.IpSecConfiguration = New-Object Microsoft.Windows.NetworkController.IpSecConfiguration   
$nwConnectionProperties.IpSecConfiguration.AuthenticationMethod = "PSK"   
$nwConnectionProperties.IpSecConfiguration.SharedSecret = "111_aaa"   

$nwConnectionProperties.IpSecConfiguration.QuickMode = New-Object Microsoft.Windows.NetworkController.QuickMode   
$nwConnectionProperties.IpSecConfiguration.QuickMode.PerfectForwardSecrecy = "PFS2048"   
$nwConnectionProperties.IpSecConfiguration.QuickMode.AuthenticationTransformationConstant = "GCMAES256"   
$nwConnectionProperties.IpSecConfiguration.QuickMode.CipherTransformationConstant = "GCMAES256"   
$nwConnectionProperties.IpSecConfiguration.QuickMode.SALifeTimeSeconds = 3600   
$nwConnectionProperties.IpSecConfiguration.QuickMode.IdleDisconnectSeconds = 500   
$nwConnectionProperties.IpSecConfiguration.QuickMode.SALifeTimeKiloBytes = 2000   

$nwConnectionProperties.IpSecConfiguration.MainMode = New-Object Microsoft.Windows.NetworkController.MainMode   
$nwConnectionProperties.IpSecConfiguration.MainMode.DiffieHellmanGroup = "Group2"   
$nwConnectionProperties.IpSecConfiguration.MainMode.IntegrityAlgorithm = "SHA256"   
$nwConnectionProperties.IpSecConfiguration.MainMode.EncryptionAlgorithm = "AES256"   
$nwConnectionProperties.IpSecConfiguration.MainMode.SALifeTimeSeconds = 28800
$nwConnectionProperties.IpSecConfiguration.MainMode.SALifeTimeKiloBytes = 2000   

# L3 specific configuration (leave blank for IPSec)  
$nwConnectionProperties.IPAddresses = @()   
$nwConnectionProperties.PeerIPAddresses = @()   

# Update the IPv4 Routes that are reachable over the site-to-site VPN Tunnel  
$nwConnectionProperties.Routes = @()   
$ipv4Route = New-Object Microsoft.Windows.NetworkController.RouteInfo   
$ipv4Route.DestinationPrefix = "<<On premise subnet that must be reachable over the VPN tunnel. Ex: 10.0.0.0/24>>"   
$ipv4Route.metric = 10   
$nwConnectionProperties.Routes += $ipv4Route   

# Tunnel Destination (Remote Endpoint) Address  
$nwConnectionProperties.DestinationIPAddress = "<<Public IP address of the On-Premise VPN gateway. Ex: 192.168.3.4>>"   

# Add the new Network Connection for the tenant. Note that the virtual gateway must be created before creating the IPsec connection. $uri is the REST URI of your deployment and must be in the form of “https://<REST URI>”  
New-NetworkControllerVirtualGatewayNetworkConnection -ConnectionUri $uri -VirtualGatewayId $virtualGW.ResourceId -ResourceId "Contoso_IPSecGW" -Properties $nwConnectionProperties -Force
```

## <a name="testing-results"></a>Результаты тестирования

Мы проделали тщательного тестирования для шлюзов SDN в лабораторных тестов производительности. В тестах мы по сравнению с сети производительность шлюза с помощью Windows Server 2019 в SDN сценарии и сценарии, отличных от SDN. Можно найти результаты и проверить сведения о настройке, записанные в статье блога [здесь](https://blogs.technet.microsoft.com/networking/2018/08/15/high-performance-gateways/).

---