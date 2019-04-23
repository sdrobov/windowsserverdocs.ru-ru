---
title: Перемещение файловых серверов в подразделение файловых серверов BranchCache
description: Этот раздел является частью BranchCache развертывания руководство для Windows Server 2016, который показывает, как развернуть BranchCache в режимах распределенный и размещенный кэш, чтобы оптимизировать использование пропускной способности глобальной сети в филиалах
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking-bc
ms.topic: get-started-article
ms.assetid: 56c915ec-edb1-43b0-8ad2-c93841bb566f
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 037b354bb6725ac7f91fc323b81bbdf15d03ac15
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59885905"
---
# <a name="move-file-servers-to-the-branchcache-file-servers-organizational-unit"></a>Перемещение файловых серверов в подразделение файловых серверов BranchCache

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

Эту процедуру можно использовать для добавления BranchCache файловых серверов с подразделением (OU) в доменных службах Active Directory (AD DS).  
  
Минимальным требованием для выполнения этой процедуры является членство в группе **Администраторы домена** или аналогичной.  
  
> [!NOTE]  
> Прежде чем добавлять учетные записи компьютеров в подразделение, с помощью этой процедуры, необходимо создать Подразделение BranchCache для файловых серверов в консоли Active Directory — пользователи и компьютеры. Дополнительные сведения см. в разделе [Создание BranchCache файл серверы подразделения](../../branchcache/deploy/Create-the-BranchCache-File-Servers-Organizational-Unit.md).  
  
### <a name="to-move-file-servers-to-the-branchcache-file-servers-organizational-unit"></a>Для перемещения файловых серверов на BranchCache файл серверы подразделения  
  
1.  На компьютере, где установлены службы AD DS в диспетчере серверов щелкните **средства**, а затем нажмите кнопку **Active Directory — пользователи и компьютеры**. Откроется консоль Active Directory — пользователи и компьютеры.  
  
2.  В консоли "Active Directory — пользователи и компьютеры" Найдите учетную запись компьютера для файлового сервера BranchCache, щелкните левой кнопкой, выберите учетную запись и затем перетаскивание учетная запись компьютера, на файловых серверах BranchCache OU, созданный ранее. Например, если вы ранее создали Подразделение с именем **BranchCache файловые серверы**перетащите учетная запись компьютера на **BranchCache файловые серверы** Подразделения.  
  
3.  Повторите предыдущий шаг для каждого файлового сервера BranchCache в домене, который требуется переместить Подразделение.  
  


