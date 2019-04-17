---
title: Перемещение файловых серверов в подразделение BranchCache файловых серверов
description: Этот раздел является частью BranchCache развертывания руководство для Windows Server 2016, которой показано, как развернуть BranchCache в режиме распределенного и размещенного кэша для оптимизации использования пропускной способности глобальной сети в филиалах
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking-bc
ms.topic: get-started-article
ms.assetid: 56c915ec-edb1-43b0-8ad2-c93841bb566f
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 09afb4936545cb1f5bb14573261008ff18badd4d
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="move-file-servers-to-the-branchcache-file-servers-organizational-unit"></a>Перемещение файловых серверов в подразделение BranchCache файловых серверов

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

Эту процедуру можно использовать для добавления файловых серверов BranchCache в организационную единицу (OU) в доменных службах Active Directory (AD DS).  
  
Членство в группе **"Администраторы домена"**, или эквивалентной группе минимальным требованием для выполнения этой процедуры.  
  
> [!NOTE]  
> Необходимо создать BranchCache файловых серверов Подразделения в консоли Active Directory-пользователи и компьютеры до добавления учетных записей компьютеров в Подразделения с помощью этой процедуры. Дополнительные сведения см. в разделе [создать BranchCache подразделения файловых серверов](../../branchcache/deploy/Create-the-BranchCache-File-Servers-Organizational-Unit.md).  
  
### <a name="to-move-file-servers-to-the-branchcache-file-servers-organizational-unit"></a>Перемещение файловых серверов для BranchCache файла подразделения серверов  
  
1.  На компьютере, где установлены Доменных службах Active Directory в диспетчере серверов щелкните **средства**, а затем нажмите кнопку **Active Directory-пользователи и компьютеры**. Откроется консоль Active Directory-пользователи и компьютеры.  
  
2.  В консоли "Active Directory-пользователи и компьютеры" Найдите учетную запись компьютера для файлового сервера BranchCache, щелчок левой кнопкой, выберите учетную запись, а затем перетаскивание учетную запись компьютера на файловых серверах BranchCache Подразделение, которое вы создали ранее. Например, если вы создали ранее организационное Подразделение с именем **файловых серверов BranchCache**, перетаскивания учетную запись компьютера на **файловых серверов BranchCache** Подразделения.  
  
3.  Повторите предыдущий шаг для каждого BranchCache файлового сервера в домене, который нужно переместить Подразделение.  
  


