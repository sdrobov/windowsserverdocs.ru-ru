---
title: Устранение проблем vRSS
description: Устраните проблемы vRSS, если вы не видите vRSS нагрузки нагрузки трафика логическим процессорам виртуальной Машины.
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
ms.sourcegitcommit: 515b4fd5c40fcbae0e12a2c30090384533972353
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/29/2018
ms.locfileid: "8232523"
---
## Устранение проблем vRSS

Если вы выполнили все шаги подготовки и по-прежнему не отображается vRSS нагрузки нагрузки трафика логическим процессорам виртуальной Машины, существуют различные потенциальные проблемы.

1. Перед выполнением действия подготовки vRSS был отключен - и теперь должен быть включен. Вы можете запустить **VMNetworkAdapter набор** для включения vRSS для виртуальной Машины.

   ```PowerShell
   Set-VMNetworkAdapter <VMname> -VrssEnabled $TRUE
   Set-VMNetworkAdapter -ManagementOS -VrssEnabled $TRUE
   ```

2. RSS была отключена в виртуальной Машине или на сетевой адаптер узла. Windows Server 2016 включает RSS по умолчанию; кто-то она могла быть отключена. 

   - Включен = **True**

   **Просмотр текущих параметров:** 

   Выполните следующий командлет PowerShell в VM\ (для vRSS в VM\) или на узле \ (для vRSS\ виртуальная сетевая карта узла).

   ```PowerShell
   Get-NetAdapterRss
   ```

   **Включите функцию:** 

   Чтобы изменить значение False значение True, запустите следующий командлет PowerShell.

   ```PowerShell
   Enable-NetAdapterRss *
   ```
   
   Другой способ системные настройки RSS использует netsh. Использование 
   
    ```cmd
   netsh int tcp show global
   ```
   
   Убедитесь, что RSS не отключен глобально. И включить ее при необходимости. Этот параметр не затронутых *-NetAdapterRSS.

3. Если вы обнаружите, что VMMQ не включен после настройки vRSS, проверьте следующие параметры на каждый адаптер, подключенный к виртуальному коммутатору:

   - VmmqEnabled = **False**
   - VmmqEnabledRequested = **True**

   ![vmmq с поддержкой](../../media/vmmq-enabled.png)

   **Просмотр текущих параметров:** 

   ```PowerShell
   Get-NetAdapterAdvancedProperty -Name NICName -DisplayName 'Virtual Switch RSS'
   ```

   **Включите функцию:** 

   ```PowerShell
   Set-NetAdapterAdvancedProperty -Name NICName -DisplayName 'Virtual Switch RSS' -DisplayValue Enabled”
   ```
 
4. _(Windows Server 2019 г.)_ Не удается включить VMMQ (VmmqEnabled = "false") при задании **VrssQueueSchedulingMode** в **динамический**. VrssQueueSchedulingMode остается неизменным в динамический, после включения VMMQ.<p>**VrssQueueSchedulingMode** из **динамического** требуется поддержка драйверов, при включении VMMQ.  VMMQ разгрузки размещения пакетов на логических процессоров и таким образом, требует поддержка драйверов для использования динамической алгоритм.  Установите поставщика Сетевых драйверов и встроенного по, который поддерживает динамические VMMQ.



---
