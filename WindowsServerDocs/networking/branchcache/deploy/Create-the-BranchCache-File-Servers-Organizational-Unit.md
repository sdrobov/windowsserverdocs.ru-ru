---
title: Создание подразделения файловых серверов BranchCache
description: Этот раздел является частью BranchCache развертывания руководство для Windows Server 2016, который показывает, как развернуть BranchCache в режимах распределенный и размещенный кэш, чтобы оптимизировать использование пропускной способности глобальной сети в филиалах
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking-bc
ms.topic: get-started-article
ms.assetid: 2cda192f-6b45-4e6c-88d9-70ca179ddb94
ms.author: pashort
author: shortpatti
ms.openlocfilehash: b7b26ec5808f5b11141e81dc5e738c83c94ef6b8
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59874085"
---
# <a name="create-the-branchcache-file-servers-organizational-unit"></a>Создание подразделения файловых серверов BranchCache

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

Эту процедуру можно использовать для создания подразделения (OU) в доменных службах Active Directory (AD DS) для BranchCache файловых серверов.  
  
Минимальным требованием для выполнения этой процедуры является членство в группе **Администраторы домена** или аналогичной.  
  
### <a name="to-create-the-branchcache-file-servers-organizational-unit"></a>Чтобы создать BranchCache файл серверы подразделения  
  
1.  На компьютере, где установлены службы AD DS в диспетчере серверов щелкните **средства**, а затем нажмите кнопку **Active Directory — пользователи и компьютеры**. Откроется консоль Active Directory — пользователи и компьютеры.  
  
2.  В консоли "Active Directory — пользователи и компьютеры" щелкните правой кнопкой мыши домен, к которому требуется добавить Подразделение. Например, если домен имеет имя example.com, щелкните правой кнопкой мыши **example.com**. Выберите команду **Создать** и щелкните **Подразделение**. **Новый объект - подразделение** откроется диалоговое окно.  
  
3.  В **новый объект - подразделение** отображаемое в диалоговом окне **имя**, введите имя нового Подразделения. Например, если требуется имя Подразделения BranchCache файловые серверы, введите **BranchCache файловые серверы**, а затем нажмите кнопку **ОК**.  
  


