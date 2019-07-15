---
title: Контроль исходящего трафика в виртуальной сети
description: 'Основным аспектом облачной сети монетизацию является возврат данных по пропускной способности сети. Пример: передача исходящих данных бизнес-модели в Microsoft Azure. Исходящие данные тарифицируются в зависимости от общего объема данных центрами обработки данных Azure через Интернет за цикл выставления счетов.'
manager: dougkim
ms.prod: windows-server-threshold
ms.technology: networking-hv-switch
ms.topic: get-started-article
ms.assetid: ''
ms.author: pashort
author: shortpatti
ms.date: 10/02/2018
ms.openlocfilehash: bdfb2b7321d5a4d119c9710e9ad93fc2e91ea536
ms.sourcegitcommit: be243a92f09048ca80f85d71555ea6ee3751d712
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67792290"
---
# <a name="egress-metering-in-a-virtual-network"></a>Измерение исходящего трафика в виртуальной сети

>Относится к: Windows Server 2019


Основным аспектом облачной сети монетизацию является возможность выставления счетов с использованием пропускной способности сети. Исходящие данные тарифицируются в зависимости от общего объема данных в центр обработки данных через Интернет за цикл выставления счетов.

Исходящие данные отслеживания использования для трафика сети SDN в Windows Server 2019 включает возможность предоставления единиц измерения использования за исходящую передачу данных. Сетевой трафик, который оставляет каждой виртуальной сети, но остается в центре обработки данных можно путем отслеживается отдельно, поэтому она может быть исключена из вычислений при выставлении счетов. Передача исходящих данных взимается ןאךוע, םאןנאגכוםםו для назначения IP-адресов, которые не находятся в одном из диапазонов адресов расчетных отслеживаются.

## <a name="virtual-network-unbilled-address-ranges-whitelist-of-ip-ranges"></a>Виртуальная сеть расчетных адресов (белый список диапазонов IP-адресов)

Вы найдете расчетных адресов в разделе **UnbilledAddressRanges** свойства существующей виртуальной сети. По умолчанию нет добавлены диапазонов адресов.

   ```PowerShell
   import-module NetworkController
   $uri = "https://sdn.contoso.com"

   (Get-NetworkControllerVirtualNetwork -ConnectionURI $URI -ResourceId "VNet1").properties
   ```

Выходные данные будут выглядеть примерно следующим образом:
   ```
    AddressSpace           : Microsoft.Windows.NetworkController.AddressSpace
    DhcpOptions            :
    UnbilledAddressRanges  :
    ConfigurationState     :
    ProvisioningState      : Succeeded
    Subnets                : {21e71701-9f59-4ee5-b798-2a9d8c2762f0, 5f4758ef-9f96-40ca-a389-35c414e996cc,
                         29fe67b8-6f7b-486c-973b-8b9b987ec8b3}
    VirtualNetworkPeerings :
    EncryptionCredential   :
    LogicalNetwork         : Microsoft.Windows.NetworkController.LogicalNetwork
   ```


## <a name="example-manage-the-unbilled-address-ranges-of-a-virtual-network"></a>Пример. Управление расчетных адресов виртуальной сети, выполните следующие действия.

Вы можете управлять набор префиксов IP-подсети для исключения из выставляется счет исходящие данные отслеживания использования, задав **UnbilledAddressRange** свойства виртуальной сети.  Любой трафик, отправленный сетевых интерфейсов в виртуальной сети с адресом назначения IP-адрес, соответствующий одному из префиксов, не будет включаться в свойстве BilledEgressBytes.

1.  Обновление **UnbilledAddressRanges** свойство может содержать подсети, которые не выставляется для доступа.

    ```PowerShell
    $vnet = Get-NetworkControllerVirtualNetwork -ConnectionUri $uri -ResourceID "VNet1"
    $vnet.Properties.UnbilledAddressRanges = "10.10.2.0/24,10.10.3.0/24"
    ```

    >[!TIP]
    >При добавлении нескольких IP-подсетей, используйте запятую между различными IP-подсетей.  Не используйте пробелы до или после запятой.

2.  Обновить ресурс виртуальной сети с измененным **UnbilledAddressRanges** свойство.

    ```PowerShell
    New-NetworkControllerVirtualNetwork -ConnectionUri $uri -ResourceId "VNet1" -Properties $unbilled.Properties -PassInnerException
    ```

    Выходные данные будут выглядеть примерно следующим образом:
      ```
         Confirm
         Performing the operation 'New-NetworkControllerVirtualNetwork' on entities of type
         'Microsoft.Windows.NetworkController.VirtualNetwork' via
         'https://sdn.contoso.com/networking/v3/virtualNetworks/VNet1'. Are you sure you want to continue?
         [Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): y


         Tags             :
         ResourceRef      : /virtualNetworks/VNet1
         InstanceId       : 29654b0b-9091-4bed-ab01-e172225dc02d
         Etag             : W/"6970d0a3-3444-41d7-bbe4-36327968d853"
         ResourceMetadata :
         ResourceId       : VNet1
         Properties       : Microsoft.Windows.NetworkController.VirtualNetworkProperties
      ```


3. Проверьте виртуальную сеть, см. в разделе настроенного **UnbilledAddressRanges**.

   ```PowerShell
   (Get-NetworkControllerVirtualNetwork -ConnectionUri $uri -ResourceID "VNet1").properties
   ```

   Выходные данные теперь будет выглядеть примерно так:
   ```
   AddressSpace           : Microsoft.Windows.NetworkController.AddressSpace
   DhcpOptions            :
   UnbilledAddressRanges  : 10.10.2.0/24,192.168.2.0/24
   ConfigurationState     :
   ProvisioningState      : Succeeded
   Subnets                : {21e71701-9f59-4ee5-b798-2a9d8c2762f0, 5f4758ef-9f96-40ca-a389-35c414e996cc,
                        29fe67b8-6f7b-486c-973b-8b9b987ec8b3}
   VirtualNetworkPeerings :
   EncryptionCredential   :
   LogicalNetwork         : Microsoft.Windows.NetworkController.LogicalNetwork
   ```

## <a name="check-the-billed-the-unbilled-egress-usage-of-a-virtual-network"></a>Проверьте по документу использования расчетных исходящий трафик виртуальной сети, выполните следующие действия.

После настройки **UnbilledAddressRanges** свойство, можно проверить использование выставляется счет и расчетных исходящий трафик каждой подсети в виртуальной сети. Исходящий трафик обновляет общее количество байтов из диапазонов, выставляется счет и начисления каждые четыре минуты.

Для каждой виртуальной подсети, доступны следующие свойства:

-   **UnbilledEgressBytes** показывает количество расчетных байтов, отправленных сетевые интерфейсы, подключенные к этой виртуальной подсети. Начисления данные представляют количество байт, отправленных диапазоны адресов, которые являются частью **UnbilledAddressRanges** свойство родительской виртуальной сети.

-   **BilledEgressBytes** показывает количество выставляется счет байтов, отправленных сетевые интерфейсы, подключенные к этой виртуальной подсети. По документу данные представляют количество байт, отправленных диапазоны адресов, которые не являются частью **UnbilledAddressRanges** свойство родительской виртуальной сети.

Используйте следующий пример для исходящего трафика использование запросов:

```PowerShell
(Get-NetworkControllerVirtualNetwork -ConnectionURI $URI -ResourceId "VNet1").properties.subnets.properties | ft AddressPrefix,BilledEgressBytes,UnbilledEgressBytes
```

Выходные данные будут выглядеть примерно следующим образом:
```
AddressPrefix BilledEgressBytes UnbilledEgressBytes
------------- ----------------- -------------------
10.0.255.8/29          16827067                   0
10.0.2.0/24           781733019                   0
10.0.4.0/24                   0                   0
```


---
