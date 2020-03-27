---
title: Создание подразделения файловых серверов BranchCache
description: Эта статья является частью руководства по развертыванию BranchCache для Windows Server 2016, в котором показано, как развернуть BranchCache в распределенном и размещенном режимах кэша для оптимизации использования пропускной способности глобальной сети в филиалах.
manager: brianlic
ms.prod: windows-server
ms.technology: networking-bc
ms.topic: get-started-article
ms.assetid: 2cda192f-6b45-4e6c-88d9-70ca179ddb94
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 40e871c25e31bbb15964d856da0f83cdaf50c48b
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80319317"
---
# <a name="create-the-branchcache-file-servers-organizational-unit"></a>Создание подразделения файловых серверов BranchCache

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

Эту процедуру можно использовать для создания подразделения (OU) в домен Active Directory Services (AD DS) для файловых серверов BranchCache.  
  
Минимальным требованием для выполнения этой процедуры является членство в группе **Администраторы домена** или аналогичной.  
  
### <a name="to-create-the-branchcache-file-servers-organizational-unit"></a>Создание подразделения файловых серверов BranchCache  
  
1.  На компьютере, где установлен AD DS, в диспетчер сервера щелкните **средства**, а затем — **Active Directory пользователи и компьютеры**. Откроется консоль Active Directory пользователи и компьютеры.  
  
2.  В консоли Active Directory пользователи и компьютеры щелкните правой кнопкой мыши домен, в который нужно добавить подразделение. Например, если домен называется example.com, щелкните правой кнопкой мыши **example.com**. Выберите команду **Создать** и щелкните **Подразделение**. Откроется диалоговое окно **новый объект — организационное подразделение** .  
  
3.  В диалоговом окне **новый объект — организационное подразделение** в поле **имя**введите имя нового подразделения. Например, если вы хотите присвоить имя серверам файловых серверов BranchCache, введите **BranchCache File Servers**и нажмите кнопку **ОК**.  
  


