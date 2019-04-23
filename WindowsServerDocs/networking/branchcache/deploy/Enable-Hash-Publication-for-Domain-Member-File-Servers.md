---
title: Включение возможности публикации хэша для файловых серверов, входящих в домен
description: Этот раздел является частью BranchCache развертывания руководство для Windows Server 2016, который показывает, как развернуть BranchCache в режимах распределенный и размещенный кэш, чтобы оптимизировать использование пропускной способности глобальной сети в филиалах
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking-bc
ms.topic: get-started-article
ms.assetid: a3f1f7c4-d9b2-43e6-8bfa-fac707bbd4d3
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 174e83c950d2aff8afba4f05641a74861b9a7938
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59865465"
---
# <a name="enable-hash-publication-for-domain-member-file-servers"></a>Включение возможности публикации хэша для файловых серверов, входящих в домен

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

При использовании доменных служб Active Directory (AD DS), чтобы включить BranchCache публикация хэша для нескольких файловых серверов можно использовать групповую политику домена. Чтобы сделать это, необходимо создать подразделение (OU), добавить файловые серверы с подразделением, создать публикацию хэша BranchCache объекта групповой политики (GPO) и затем настроить объект групповой Политики.  
  
См. в разделах, чтобы включить публикацию хэшей для нескольких файловых серверов.  
  
-   [Создание подразделения серверов файлов BranchCache](../../branchcache/deploy/Create-the-BranchCache-File-Servers-Organizational-Unit.md)  
  
-   [Перемещение файловых серверов организационное подразделение серверы файл BranchCache](../../branchcache/deploy/Move-File-Servers-to-the-BranchCache-File-Servers-Organizational-Unit.md)  
  
-   [Создайте объект BranchCache хэш публикации групповой политики](../../branchcache/deploy/Create-the-BranchCache-Hash-Publication-Group-Policy-Object.md)  
  
-   [Настройте объект BranchCache хэш публикации групповой политики](../../branchcache/deploy/Configure-the-BranchCache-Hash-Publication-Group-Policy-Object.md)  
  


