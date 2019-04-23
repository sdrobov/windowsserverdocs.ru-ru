---
title: Команды Windows PowerShell для RSS и vRSS
description: В этом разделе вы узнаете, как быстро найти технические справочные сведения о командах Windows PowerShell на стороне приема масштабирование (RSS) и виртуальных RSS (vRSS).
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
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59833265"
---
# <a name="windows-powershell-commands-for-rss-and-vrss"></a>Команды Windows PowerShell для RSS и vRSS

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

В этом разделе вы узнаете, как быстро найти технические справочные сведения о командах Windows PowerShell для масштабирования на стороне приема \(RSS\) и виртуальный RSS \(vRSS\).

Используйте следующие команды RSS настройку RSS на физическом компьютере с несколькими процессорами или несколькими ядрами. Чтобы настроить vRSS на виртуальной машине можно использовать те же команды \(виртуальной Машины\) , под управлением поддерживаемой операционной системы. Дополнительные сведения см. в разделе [командлеты сетевого адаптера в Windows PowerShell](https://docs.microsoft.com/powershell/module/netadapter/?view=win10-ps).

## <a name="configure-vmq"></a>Настроить VMQ

vRSS требует, что VMQ включена и настроена. Можно использовать следующие команды Windows PowerShell для управления параметрами VMQ.

- [Disable-NetAdapterVmq](https://docs.microsoft.com/powershell/module/netadapter/disable-netadaptervmq?view=win10-ps)
- [Enable-NetAdapterVmq](https://docs.microsoft.com/powershell/module/netadapter/enable-netadaptervmq?view=win10-ps)
- [Get-NetAdapterVmq](https://docs.microsoft.com/powershell/module/netadapter/get-netadaptervmq?view=win10-ps)
- [SET-NetAdapterVmq](https://docs.microsoft.com/powershell/module/netadapter/set-netadaptervmq?view=win10-ps)

## <a name="enable-and-configure-rss-on-a-native-host"></a>Включение и настройка RSS на собственном узле

Используйте следующие команды PowerShell Настройка RSS на собственном узле, а также управление RSS на виртуальной Машине или на узле виртуальный сетевой Адаптер (vNIC). Некоторые параметры из этих команд может также повлиять на очередь виртуальных машин \(VMQ\) на узле Hyper-V.  

>[!IMPORTANT]
>Включение RSS на виртуальной Машине или на виртуальный сетевой адаптер узла является необходимым условием для активации и использовании vRSS.

- [Disable-NetAdapterRss](https://docs.microsoft.com/powershell/module/netadapter/disable-netadapterrss?view=win10-ps)
- [Enable-NetAdapterRss](https://docs.microsoft.com/powershell/module/netadapter/enable-netadapterrss?view=win10-ps)
- [Get-NetAdapterRss](https://docs.microsoft.com/powershell/module/netadapter/get-netadapterrss?view=win10-ps)
- [SET-NetAdapterRss](https://docs.microsoft.com/powershell/module/netadapter/Set-NetAdapterRss?view=win10-ps)

## <a name="enable-vrss-on-the-hyper-v-virtual-switch-port"></a>Включите vRSS на Hyper\-порта V виртуального коммутатора

Помимо возможности RSS на виртуальной машине, vRSS необходимо включить vRSS на Hyper\-порта V виртуального коммутатора. 

Определите присутствуют параметры для vRSS и включить или отключить эту функцию для виртуальной Машины.

   **Просмотрите текущие параметры:** 

   ```PowerShell
   Get-VMNetworkAdapter <vm-name> | fl
   ```

   **Включена функция:**
   
   ```PowerShell
   Set-VMNetworkAdapter <vm-name> -VrssEnabled [$True|$False]
   ```

## <a name="enable-or-disable-vrss-on-a-host-vnic"></a>Включение или отключение vRSS на виртуальный сетевой адаптер узла

Определите присутствуют параметры для vRSS и включить или отключить этот компонент для виртуального сетевого адаптера узла.

   **Просмотрите текущие параметры:** 

   ```PowerShell
   Get-VMNetworkAdapter -ManagementOS | fl
   ```

   **Включить или отключить эту функцию:** 

   ```PowerShell
   Set-VMNetworkAdapter -ManagementOS -VrssEnabled [$True|$False]
   ```

## <a name="configure-the-scheduling-mode-on-the-hyper-v-virtual-switch-port"></a>Настройте режим планирования через порт виртуального коммутатора Hyper-V 
>Относится к: Windows Server 2019

В Windows Server 2019 vRSS можно обновить логических процессоров, используемых для обработки сетевого трафика, динамически.  Устройства с помощью поддерживаемых драйверов имеют этот планирования режим включен по умолчанию. 

Определение режима планирования работы присутствует в системе или измените режим планирования для виртуальной Машины.

   **Просмотрите текущие параметры:** 

   ```PowerShell
   Get-VMNetworkAdapter <vm-name> | Select 'VRSSQueue'
   ```

   **Задать или изменить режим планирования:**

   ```PowerShell
   Set-VMNetworkAdapter <vm-name> -VrssQueueSchedulingMode [Dynamic|$StaticVrss|StaticVMQ]
   ```

## <a name="configure-the-scheduling-mode-on-a-host-vnic"></a>Настройте режим планирования на виртуальный сетевой адаптер узла
>Относится к: Windows Server 2019

Чтобы определить, существует режим планирования или изменить режим планирования для виртуального сетевого адаптера узла, используйте следующие команды Windows PowerShell:

   **Просмотрите текущие параметры:** 

   ```PowerShell
   Get-VMNetworkAdapter -ManagementOS | Select 'VRSSQueue'
   ```

   **Задать или изменить режим планирования:** 

   ```PowerShell
   Set-VMNetworkAdapter -ManagementOS -VrssQueueSchedulingMode -VrssQueueSchedulingMode [Dynamic|$StaticVrss|StaticVMQ]
   ```


## <a name="related-topics"></a>См. также 
Дополнительные сведения см. в следующих справочных разделах.

- [Get-VMNetworkAdapter](https://technet.microsoft.com/itpro/powershell/windows/hyper-v/get-vmnetworkadapter)
- [SET-VMNetworkAdapter](https://technet.microsoft.com/itpro/powershell/windows/hyper-v/set-vmnetworkadapter)

Дополнительные сведения см. в разделе [виртуального масштабирования на стороне приема (vRSS)](vrss-top.md).