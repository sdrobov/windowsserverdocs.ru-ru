---
title: Управление vRSS
description: В этом разделе вы команды Windows PowerShell для управления vRSS в виртуальных машин (ВМ), а также на узлах Hyper-V.
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: 0fe5bfc3-591f-4a19-b98a-0668d4c9f93a
ms.localizationpriority: medium
manager: dougkim
ms.date: 09/05/2018
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 8af800608bee7037b48141a7a2edb0c872a7aac0
ms.sourcegitcommit: e84e328c13a701e8039b16a4824a6e58a6e59b0b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2018
ms.locfileid: "4133840"
---
# Управление vRSS

В этом разделе вы команды Windows PowerShell для управления vRSS в \(VMs\) виртуальные машины и на узлах Hyper-V.

>[!NOTE]
>Дополнительные сведения о командах, упомянутых в этом разделе см. в разделе [Команды Windows PowerShell для RSS-Каналов и vRSS](vrss-wps.md).

## VMQ на узлах Hyper-V

На узле Hyper-V необходимо использовать ключевые слова, управляющие VMQ процессоров.

**Просмотр текущих параметров:** 

```PowerShell
Get-NetAdapterVmq
```

**Настройте параметры VMQ:** 

```PowerShell
Set-NetAdapterVmq
```


## порты коммутатора vRSS в Hyper-V

На узле Hyper-V необходимо также включить vRSS порт виртуального коммутатора Hyper-V.

**Просмотр текущих параметров:**

```PowerShell
Get-VMNetworkAdapter <vm-name> | fl

Get-VMNetworkAdapter -ManagementOS | fl
```
    
Оба следующие параметры должны иметь **значение True**. 

- VrssEnabledRequested: True
- VrssEnabled: True
    
>[!IMPORTANT]
>В некоторых условиях ресурсов ограничение порт виртуального коммутатора Hyper-V может быть не удается установить эта функция включена. Это условие временные, и функцию может стать доступной более поздний момент.
>
>Если **VrssEnabled** имеет **значение True**, то эта функция включается для этого порта виртуального коммутатора Hyper-V — то есть для данной виртуальной Машины или сетевой адаптер управления.

**Настройте параметры vRSS порт переключателя:**

```PowerShell
Set-VMNetworkAdapter <vm-name> -VrssEnabled $TRUE
    
Set-VMNetworkAdapter -ManagementOS -VrssEnabled $TRUE
```

## vRSS в виртуальных машинах и виртуальные сетевые карты узла

Можно использовать те же команды, используемые для собственных RSS для настройки vRSS в виртуальных машинах и виртуальные сетевые карты узла, который также является способ включения RSS на виртуальные сетевые карты узла.  

**Просмотр текущих параметров:**

```PowerShell
Get-NetAdapterRSS
```

**Настройка параметров vRSS:**

```PowerShell
Set-NetAdapterRss
```

>[!NOTE]
> Параметр профиля внутри виртуальной Машины не влияет на планирование работы. Hyper-V делает всех решений по планированию и игнорирует профиля внутри виртуальной Машины.

## Отключить vRSS

Вы можете отключить vRSS для отключения любого из ранее упомянутое параметров.

- Отключение VMQ для физическому сетевому Адаптеру или виртуальной Машине.

  >[!CAUTION]
  >Отключение VMQ на физический сетевой Адаптер серьезно влияет возможность вашего узла Hyper-V для обработки входящих пакетов.

- Отключение vRSS для виртуальной Машины на порт виртуального коммутатора Hyper-V на узле Hyper-V.

   ```PowerShell
   Set-VMNetworkAdapter <vm-name> -VrssEnabled $FALSE
   ```

- Отключите vRSS для виртуальный сетевой адаптер узла порт виртуального коммутатора Hyper-V на узле Hyper-V.

   ```PowerShell
   Set-VMNetworkAdapter -ManagementOS -VrssEnabled $FALSE
   ```

- Отключить RSS в виртуальной Машине \(or host vNIC\) внутри виртуальной Машины \ (или host\)

   ```PowerShell
   Disable-NetAdapterRSS *
   ```
