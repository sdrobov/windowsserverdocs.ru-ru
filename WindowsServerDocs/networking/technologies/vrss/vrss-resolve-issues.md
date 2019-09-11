---
title: Устранение проблем vRSS
description: Устраните проблемы vRSS, если вы не видите трафик балансировки нагрузки vRSS для виртуальной машины LPs.
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: ''
ms.localizationpriority: medium
manager: dougkim
ms.author: pashort
author: shortpatti
ms.date: 09/04/2018
ms.openlocfilehash: 412f24e25f75b390ac6315609705b463548c4345
ms.sourcegitcommit: f6490192d686f0a1e0c2ebe471f98e30105c0844
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70871813"
---
## <a name="resolve-vrss-issues"></a>Устранение проблем vRSS

Если вы выполнили все подготовительные действия и вы по-прежнему не видите трафик балансировки нагрузки vRSS для виртуальной машины LPs, возможны различные проблемы.

1. Перед выполнением подготовительных действий vRSS было отключено, и теперь оно должно быть включено. Чтобы включить vRSS для виртуальной машины, можно выполнить команду **Set-VMNetworkAdapter** .

   ```PowerShell
   Set-VMNetworkAdapter <VMname> -VrssEnabled $TRUE
   Set-VMNetworkAdapter -ManagementOS -VrssEnabled $TRUE
   ```

2. RSS отключен в виртуальной машине или на узле vNIC. Windows Server 2016 включает RSS по умолчанию; возможно, кто-то отключил его. 

   - Enabled = **true**

   **Просмотр текущих параметров:** 

   Выполните следующий командлет PowerShell\(на виртуальной машине для vrss на виртуальной машине\) или на узле \(для vNIC узла vrss\).

   ```PowerShell
   Get-NetAdapterRss
   ```

   **Включите функцию:** 

   Чтобы изменить значение false на true, выполните следующий командлет PowerShell.

   ```PowerShell
   Enable-NetAdapterRss *
   ```
   
   Другим системным способом настройки RSS является использование Netsh. Используйте 
   
    ```cmd
   netsh int tcp show global
   ```
   
   чтобы убедиться, что RSS не отключен глобально. И при необходимости включите его. Этот параметр не затронут *-Нетадаптеррсс.

3. Если после настройки vRSS обнаруживается ВММК, проверьте следующие параметры на каждом адаптере, подключенном к виртуальному коммутатору:

   - Вммкенаблед = **false**
   - Вммкенабледрекуестед = **true**

   ![вммк — включено](../../media/vmmq-enabled.png)

   **Просмотр текущих параметров:** 

   ```PowerShell
   Get-NetAdapterAdvancedProperty -Name NICName -DisplayName 'Virtual Switch RSS'
   ```

   **Включите функцию:** 

   ```PowerShell
   Set-NetAdapterAdvancedProperty -Name NICName -DisplayName 'Virtual Switch RSS' -DisplayValue Enabled”
   ```
 
4. _(Windows Server 2019)_ Невозможно включить ВММК (Вммкенаблед = false) при задании для **врсскуеуесчедулингмоде** значения **dynamic**. Врсскуеуесчедулингмоде не меняется на Dynamic после включения ВММК.<p>**Врсскуеуесчедулингмоде** **динамического** требует поддержки драйвера при включенном вммк.  ВММК — это разгрузка размещения пакетов на логических процессорах и поэтому требует поддержки драйверов для использования динамического алгоритма.  Установите драйвер и встроенное по поставщика сетевых карт, поддерживающее динамическое ВММК.



---
