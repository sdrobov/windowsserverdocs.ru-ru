---
title: Создание подразделения BranchCache файловых серверов
description: Этот раздел является частью BranchCache развертывания руководство для Windows Server 2016, которой показано, как развернуть BranchCache в режиме распределенного и размещенного кэша для оптимизации использования пропускной способности глобальной сети в филиалах
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking-bc
ms.topic: get-started-article
ms.assetid: 2cda192f-6b45-4e6c-88d9-70ca179ddb94
ms.author: pashort
author: shortpatti
ms.openlocfilehash: a92cb3110e4aecb1ef09a45ed14173305722c655
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="create-the-branchcache-file-servers-organizational-unit"></a>Создание подразделения BranchCache файловых серверов

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

Эту процедуру можно использовать для создания подразделения (OU) в доменных службах Active Directory (AD DS) для файловых серверов BranchCache.  
  
Членство в группе **"Администраторы домена"**, или эквивалентной группе минимальным требованием для выполнения этой процедуры.  
  
### <a name="to-create-the-branchcache-file-servers-organizational-unit"></a>Чтобы создать BranchCache подразделения файловых серверов  
  
1.  На компьютере, где установлены Доменных службах Active Directory в диспетчере серверов щелкните **средства**, а затем нажмите кнопку **Active Directory-пользователи и компьютеры**. Откроется консоль Active Directory-пользователи и компьютеры.  
  
2.  В консоли "Active Directory-пользователи и компьютеры" щелкните правой кнопкой мыши домен, к которому требуется добавить Подразделение. Например, если ваш домен называется example.com, щелкните правой кнопкой мыши **example.com**. Наведите курсор на **New**, а затем нажмите кнопку **подразделение**. **Новый объект - подразделение** откроется диалоговое окно.  
  
3.  В **новый объект - подразделение** диалогового окна **имя**, введите имя нового Подразделения. Например, если необходимо присвоить имя BranchCache Подразделение файловых серверов, введите **файловых серверов BranchCache**, а затем нажмите кнопку **ОК**.  
  


