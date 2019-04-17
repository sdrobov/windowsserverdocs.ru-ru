---
title: Включение возможности публикации хэша для файловых серверов домена
description: Этот раздел является частью BranchCache развертывания руководство для Windows Server 2016, которой показано, как развернуть BranchCache в режиме распределенного и размещенного кэша для оптимизации использования пропускной способности глобальной сети в филиалах
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking-bc
ms.topic: get-started-article
ms.assetid: a3f1f7c4-d9b2-43e6-8bfa-fac707bbd4d3
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 318879eae82d37f68acbc18cdb21ae5290f6d02b
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="enable-hash-publication-for-domain-member-file-servers"></a>Включение возможности публикации хэша для файловых серверов домена

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

При использовании доменных служб Active Directory (AD DS), можно использовать групповую политику домена для Включение возможности публикации хэша BranchCache для нескольких файловых серверов. Чтобы сделать это, необходимо создать подразделение (OU), добавьте в Подразделение файловых серверов, создание публикации хэша BranchCache объекта групповой политики (GPO) и затем настройте объект групповой Политики.  
  
Включение возможности публикации хэша для нескольких файловых серверов с в следующих разделах.  
  
-   [Создание подразделения BranchCache файловых серверов](../../branchcache/deploy/Create-the-BranchCache-File-Servers-Organizational-Unit.md)  
  
-   [Перемещение файловых серверов в подразделение BranchCache файловых серверов](../../branchcache/deploy/Move-File-Servers-to-the-BranchCache-File-Servers-Organizational-Unit.md)  
  
-   [Создание объекта политики группа публикации хэша BranchCache](../../branchcache/deploy/Create-the-BranchCache-Hash-Publication-Group-Policy-Object.md)  
  
-   [Настройка хэш публикации объекта групповой политики BranchCache](../../branchcache/deploy/Configure-the-BranchCache-Hash-Publication-Group-Policy-Object.md)  
  


