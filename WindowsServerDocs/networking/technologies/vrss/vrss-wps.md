---
title: Команды Windows PowerShell для RSS-Каналов и vRSS
description: В этом разделе вы узнаете, как быстро находить технические сведения о команды Windows PowerShell для масштабирования получать стороне (RSS) и виртуальные RSS (vRSS).
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: 49e93b9f-46d9-4cee-bcda-1c4634893ddd
ms.localizationpriority: medium
manager: dougkim
ms.author: pashort
author: shortpatti
ms.date: 09/05/2018
ms.openlocfilehash: 10039388009e32c10d71067b835bad65db5607ef
ms.sourcegitcommit: 9ed4c9fe04ebf3ef488170503c9a354c992b6fde
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2018
ms.locfileid: "4339272"
---
# Команды Windows PowerShell для RSS-Каналов и vRSS

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

В этом разделе вы узнаете, как быстро находить технические сведения о команды Windows PowerShell для \(RSS\) масштабирование на стороне приема и виртуальные \(vRSS\) RSS.

Используйте следующие команды RSS для настройки RSS на физическом компьютере с несколькими процессорами или несколькими ядрами. Те же команды можно использовать для настройки vRSS на виртуальной машине \(VM\) под управлением поддерживаемой операционной системы. Дополнительные сведения см. в разделе [Командлеты сетевых адаптеров в Windows PowerShell](https://docs.microsoft.com/powershell/module/netadapter/?view=win10-ps).

## Настройка VMQ

vRSS требует, что VMQ включен и настроен. Можно использовать следующие команды Windows PowerShell для управления параметрами VMQ.

- [Отключение NetAdapterVmq](https://docs.microsoft.com/powershell/module/netadapter/disable-netadaptervmq?view=win10-ps)
- [Enable-NetAdapterVmq](https://docs.microsoft.com/powershell/module/netadapter/enable-netadaptervmq?view=win10-ps)
- [Get-NetAdapterVmq](https://docs.microsoft.com/powershell/module/netadapter/get-netadaptervmq?view=win10-ps)
- [SET-NetAdapterVmq](https://docs.microsoft.com/powershell/module/netadapter/set-netadaptervmq?view=win10-ps)

## Включение и настройка RSS в собственной узла

Используйте следующие команды PowerShell для настройки RSS на собственных узле, а также управлять RSS в виртуальной Машине или на узле виртуальный сетевой Адаптер (vNIC). Некоторые параметры из этих команд также может повлиять на \(VMQ\) очереди виртуальной машины на узле Hyper-V.  

>[!IMPORTANT]
>Включение RSS в виртуальной Машине или на виртуальный сетевой адаптер узла является обязательным требованием для включения и использования vRSS.

- [Отключение NetAdapterRss](https://docs.microsoft.com/powershell/module/netadapter/disable-netadapterrss?view=win10-ps)
- [Enable-NetAdapterRss](https://docs.microsoft.com/powershell/module/netadapter/enable-netadapterrss?view=win10-ps)
- [Get-NetAdapterRss](https://docs.microsoft.com/powershell/module/netadapter/get-netadapterrss?view=win10-ps)
- [SET-NetAdapterRss](https://docs.microsoft.com/powershell/module/netadapter/Set-NetAdapterRss?view=win10-ps)

## Включение vRSS порт виртуального коммутатора Hyper-V

Помимо включения RSS в виртуальной Машине, vRSS требуется включить vRSS порт виртуального коммутатора Hyper-V. 

Параметров для vRSS и включить или отключить функцию для виртуальной Машины.

   **Просмотр текущих параметров:** 

   ```PowerShell
   Get-VMNetworkAdapter <vm-name> | fl
   ```

   **Включена функция:**
   
   ```PowerShell
   Set-VMNetworkAdapter <vm-name> -VrssEnabled [$True|$False]
   ```

## Включение и отключение vRSS на виртуальный сетевой адаптер узла

Параметров для vRSS и включить или отключить функцию для сетевой адаптер узла.

   **Просмотр текущих параметров:** 

   ```PowerShell
   Get-VMNetworkAdapter -ManagementOS | fl
   ```

   **Включить или отключить функцию:** 

   ```PowerShell
   Set-VMNetworkAdapter -ManagementOS -VrssEnabled [$True|$False]
   ```

## Настроить режим планирования порт виртуального коммутатора Hyper-V 
>Область применения: Windows Server 2019 г.

В Windows Server 2019 vRSS можно обновить логических процессоров, используемых для обработки сетевого трафика динамически.  Устройства с помощью поддерживаемых драйверов имеют этот планирования режим включен по умолчанию. 

Определения присутствует планирования режима в системе, или изменить планирования режим для виртуальной Машины.

   **Просмотр текущих параметров:** 

   ```PowerShell
   Get-VMNetworkAdapter <vm-name> | Select 'VRSSQueue'
   ```

   **Установить или изменить режим планирования:**

   ```PowerShell
   Set-VMNetworkAdapter <vm-name> -VrssQueueSchedulingMode [Dynamic|$StaticVrss|StaticVMQ]
   ```

## Настройка режима планирования на виртуальный сетевой адаптер узла
>Область применения: Windows Server 2019 г.

Чтобы определить, есть режим планирования или изменить планирования режим для сетевой адаптер узла, используйте следующие команды Windows PowerShell:

   **Просмотр текущих параметров:** 

   ```PowerShell
   Get-VMNetworkAdapter -ManagementOS | Select 'VRSSQueue'
   ```

   **Установить или изменить режим планирования:** 

   ```PowerShell
   Set-VMNetworkAdapter -ManagementOS -VrssQueueSchedulingMode -VrssQueueSchedulingMode [Dynamic|$StaticVrss|StaticVMQ]
   ```


## Еще по теме 
Дополнительные сведения см. в следующих разделах.

- [Get-VMNetworkAdapter](https://technet.microsoft.com/itpro/powershell/windows/hyper-v/get-vmnetworkadapter)
- [SET-VMNetworkAdapter](https://technet.microsoft.com/itpro/powershell/windows/hyper-v/set-vmnetworkadapter)

Дополнительные сведения см. в разделе [Виртуальных масштабирование на стороне приема (vRSS)](vrss-top.md).