---
title: Устранение проблем vRSS
description: Устраните ошибки vRSS, если вы не видите Балансировка нагрузки трафика для виртуальной Машины LPs vRSS.
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: ''
ms.localizationpriority: medium
manager: dougkim
ms.author: pashort
author: shortpatti
ms.date: 09/04/2018
ms.openlocfilehash: a2d6eb43149361b4270565b63fc99f483f364f74
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59824035"
---
## <a name="resolve-vrss-issues"></a>Устранение проблем vRSS

Если вы выполнили все действия по подготовке и вы по-прежнему не видите Балансировка нагрузки трафика для виртуальной Машины LPs vRSS, существуют различные возможные причины этой проблемы.

1. Прежде чем вы выполнили действия по подготовке, vRSS был отключен — и теперь должна быть включена. Можно запустить **Set-VMNetworkAdapter** для включения vRSS для виртуальной Машины.

   ```PowerShell
   Set-VMNetworkAdapter <VMname> -VrssEnabled $TRUE
   Set-VMNetworkAdapter -ManagementOS -VrssEnabled $TRUE
   ```

2. RSS была отключена на виртуальной машине или на виртуальном сетевом адаптере узла. Windows Server 2016 включает RSS по умолчанию; кто-то возможно она отключена. 

   - Включена = **True**

   **Просмотрите текущие параметры:** 

   Запустите следующий командлет PowerShell на виртуальной Машине\(для vRSS на виртуальной Машине\) или на узле \(для vRSS виртуального сетевого адаптера узла\).

   ```PowerShell
   Get-NetAdapterRss
   ```

   **Включите функцию:** 

   Чтобы изменить значение с False на True, выполните следующий командлет PowerShell.

   ```PowerShell
   Enable-NetAdapterRss *
   ```
   
   Другой способ общесистемные настройку RSS — использовать netsh. Используйте 
   
    ```cmd
   netsh int tcp show global
   ```
   
   Чтобы убедиться, что RSS не отключен глобально. И включите его при необходимости. Этот параметр не охваченные *-NetAdapterRSS.

3. Если вы обнаружите, что после настройки vRSS VMMQ не включен, проверьте следующие параметры для каждого адаптера, подключенного к виртуальному коммутатору:

   - VmmqEnabled = **False**
   - VmmqEnabledRequested = **True**

   ![с поддержкой vmmq](../../media/vmmq-enabled.png)

   **Просмотрите текущие параметры:** 

   ```PowerShell
   Get-NetAdapterAdvancedProperty -Name NICName -DisplayName 'Virtual Switch RSS'
   ```

   **Включите функцию:** 

   ```PowerShell
   Set-NetAdapterAdvancedProperty -Name NICName -DisplayName 'Virtual Switch RSS' -DisplayValue Enabled”
   ```
 
4. _(Windows Server 2019 г.)_  Вы не сможете включить VMMQ (VmmqEnabled = False) хотя параметр **VrssQueueSchedulingMode** для **динамическое**. VrssQueueSchedulingMode остается неизменным на динамический, после включения VMMQ.<p>**VrssQueueSchedulingMode** из **динамическое** требуется поддержка драйверов, при включении VMMQ.  VMMQ разгрузки размещение пакетов на логических процессорах и таким образом, требует поддержки драйвера, чтобы использовать динамический алгоритм.  Установите драйвер и встроенное по с поддержкой динамического VMMQ поставщика сетевой Адаптер.



---
