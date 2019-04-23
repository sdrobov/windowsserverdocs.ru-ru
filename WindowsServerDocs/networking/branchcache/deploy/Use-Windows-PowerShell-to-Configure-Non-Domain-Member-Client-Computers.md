---
title: Настройка входящих в домен клиентских компьютеров с помощью Windows PowerShell
description: Этот раздел является частью BranchCache развертывания руководство для Windows Server 2016, который показывает, как развернуть BranchCache в режимах распределенный и размещенный кэш, чтобы оптимизировать использование пропускной способности глобальной сети в филиалах
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking-bc
ms.topic: get-started-article
ms.assetid: 1b511e1a-686d-441f-a1c7-d4d029e1a061
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 9abb77e573d7b3f144ab831c655c81370a4a6af1
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59839955"
---
# <a name="use-windows-powershell-to-configure-non-domain-member-client-computers"></a>Настройка входящих в домен клиентских компьютеров с помощью Windows PowerShell

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

Эту процедуру можно использовать для ручной настройки клиентского компьютера BranchCache для режима распределенного кэша, или в режиме размещенного кэша.  
  
> [!NOTE]  
> Если вы настроили клиентских компьютеров BranchCache, с помощью групповой политики, параметры групповой политики переопределяют любые ручные настройки клиентских компьютеров, к которым применены политики.  
  
Членство в группе **Администраторы**, или эквивалентной является минимальным требованием для выполнения этой процедуры.  
  
### <a name="to-enable-branchcache-distributed-or-hosted-cache-mode"></a>Чтобы включить режим распределенного или размещенного кэша BranchCache  
  
1.  На компьютере клиента BranchCache, который вы хотите настроить запустите Windows PowerShell от имени администратора и выполните одно из следующих.  
  
    -   Чтобы настроить клиентский компьютер для режима распределенного кэша BranchCache, введите следующую команду и нажмите клавишу ВВОД.  
  
        `Enable-BCDistributed`  
  
    -   Чтобы настроить клиентский компьютер для режима BranchCache размещенного кэша, введите следующую команду и нажмите клавишу ВВОД.  
  
        `Enable-BCHostedClient`  
  
        > [!TIP]  
        > Если вы хотите указать серверы размещенного кэша, доступен, используйте `-ServerNames` параметр с разделителями запятыми список серверов размещенного кэша в качестве значения параметра. Например если у вас есть два сервера размещенного кэша с именем HCS1 и HCS2, Настройка клиентского компьютера режим размещенного кэша с помощью следующей команды.  
        >   
        > `Enable-BCHostedClient -ServerNames HCS1,HCS2`  
  


