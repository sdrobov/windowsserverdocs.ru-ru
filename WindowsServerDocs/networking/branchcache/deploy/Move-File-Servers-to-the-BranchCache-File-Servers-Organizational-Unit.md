---
title: Перемещение файловых серверов в подразделение файловых серверов BranchCache
description: Эта статья является частью руководства по развертыванию BranchCache для Windows Server 2016, в котором показано, как развернуть BranchCache в распределенном и размещенном режимах кэша для оптимизации использования пропускной способности глобальной сети в филиалах.
manager: brianlic
ms.prod: windows-server
ms.technology: networking-bc
ms.topic: get-started-article
ms.assetid: 56c915ec-edb1-43b0-8ad2-c93841bb566f
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 045764f9ed7cb7eef5a996748e293b48ec6018fb
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80319205"
---
# <a name="move-file-servers-to-the-branchcache-file-servers-organizational-unit"></a>Перемещение файловых серверов в подразделение файловых серверов BranchCache

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

Эту процедуру можно использовать для добавления файловых серверов BranchCache в подразделение (OU) в домен Active Directory Services (AD DS).  
  
Минимальным требованием для выполнения этой процедуры является членство в группе **Администраторы домена** или аналогичной.  
  
> [!NOTE]  
> Перед добавлением учетных записей компьютеров в подразделение с помощью этой процедуры необходимо создать подразделение файловых серверов BranchCache в консоли Active Directory пользователи и компьютеры. Дополнительные сведения см. [в разделе Создание подразделения файловых серверов BranchCache](../../branchcache/deploy/Create-the-BranchCache-File-Servers-Organizational-Unit.md).  
  
### <a name="to-move-file-servers-to-the-branchcache-file-servers-organizational-unit"></a>Перемещение файловых серверов в организационное подразделение файловых серверов BranchCache  
  
1.  На компьютере, где установлен AD DS, в диспетчер сервера щелкните **средства**, а затем — **Active Directory пользователи и компьютеры**. Откроется консоль Active Directory пользователи и компьютеры.  
  
2.  В консоли Active Directory пользователи и компьютеры найдите учетную запись компьютера для файлового сервера BranchCache, щелкните ее левой кнопкой мыши, чтобы выбрать учетную запись, а затем перетащите учетную запись компьютера в созданном ранее подразделении файловых серверов BranchCache. Например, если вы ранее создали подразделение с именем **файловые серверы BranchCache**, перетащите учетную запись компьютера в подразделении **файловых серверов BranchCache** .  
  
3.  Повторите предыдущий шаг для каждого файлового сервера BranchCache в домене, который необходимо переместить в подразделение.  
  


