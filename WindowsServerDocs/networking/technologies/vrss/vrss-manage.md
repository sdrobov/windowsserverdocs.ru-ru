---
title: Управление vRSS
description: В этом разделе вы команды Windows PowerShell для управления vRSS на виртуальных машинах (ВМ) и на узлах Hyper-V.
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
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59856195"
---
# <a name="manage-vrss"></a>Управление vRSS

В этом разделе, используйте команды Windows PowerShell для управления vRSS на виртуальных машинах \(виртуальных машин\) и на Hyper\-узлов V.

>[!NOTE]
>Дополнительные сведения о командах, упомянутых в этом разделе, см. в разделе [команды Windows PowerShell для RSS и vRSS](vrss-wps.md).

## <a name="vmq-on-hyper-v-hosts"></a>VMQ на узлах Hyper-V

На узле Hyper-V необходимо использовать ключевые слова, управляющие процессорами VMQ.

**Просмотрите текущие параметры:** 

```PowerShell
Get-NetAdapterVmq
```

**Настройте параметры VMQ.** 

```PowerShell
Set-NetAdapterVmq
```


## <a name="vrss-on-hyper-v-switch-ports"></a>порты коммутатора vRSS на узле Hyper-V

На узле Hyper-V, необходимо также включить vRSS на Hyper\-порта V виртуального коммутатора.

**Просмотрите текущие параметры:**

```PowerShell
Get-VMNetworkAdapter <vm-name> | fl

Get-VMNetworkAdapter -ManagementOS | fl
```
    
Оба из следующих параметров, должны быть **True**. 

- VrssEnabledRequested: True
- VrssEnabled: True
    
>[!IMPORTANT]
>В некоторых условиях ресурсов ограничение Hyper\-порт виртуального коммутатора V возможно включение этой функции. Это временное состояние, и функции могут стать доступны в последующее время.
>
>Если **VrssEnabled** — **True**, затем эта функция включена для этого Hyper\-порт виртуального коммутатора V — то есть для этой виртуальной Машины или виртуальный сетевой адаптер.

**Настройте параметры vRSS порт коммутатора.**

```PowerShell
Set-VMNetworkAdapter <vm-name> -VrssEnabled $TRUE
    
Set-VMNetworkAdapter -ManagementOS -VrssEnabled $TRUE
```

## <a name="vrss-in-vms-and-host-vnics"></a>vRSS в виртуальные машины и виртуальные сетевые карты узла

Можно использовать те же команды, используется для собственного для настройки vRSS в виртуальные машины и виртуальные сетевые карты узла, который также является способ включить RSS на виртуальные сетевые карты узла.  

**Просмотрите текущие параметры:**

```PowerShell
Get-NetAdapterRSS
```

**Настройте параметры vRSS.**

```PowerShell
Set-NetAdapterRss
```

>[!NOTE]
> Настройка профиля в рамках виртуальной Машины не влияет на планирование работы. Hyper\-V делает все планирования решения и игнорирует профиль в рамках виртуальной Машины.

## <a name="disable-vrss"></a>Отключить vRSS

Вы можете отключить vRSS для отключения любой из приведенных выше параметров.

- Отключите VMQ для физический сетевой Адаптер или виртуальной Машины.

  >[!CAUTION]
  >Отключить VMQ на физический сетевой Адаптер серьезно влияет на способность Hyper\-V узла для обработки входящих пакетов.

- Отключить vRSS для виртуальных Машин в Hyper\-порту Hyper V виртуальный коммутатор\-узел V.

   ```PowerShell
   Set-VMNetworkAdapter <vm-name> -VrssEnabled $FALSE
   ```

- Отключить vRSS для виртуального сетевого адаптера узла на Hyper\-порту Hyper V виртуальный коммутатор\-узел V.

   ```PowerShell
   Set-VMNetworkAdapter -ManagementOS -VrssEnabled $FALSE
   ```

- Отключить RSS на виртуальной машине \(или виртуальный сетевой адаптер узла\) на виртуальную машину \(или на узле\)

   ```PowerShell
   Disable-NetAdapterRSS *
   ```
