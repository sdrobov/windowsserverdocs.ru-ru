---
title: Включение возможности публикации хэша для файловых серверов, входящих в домен
description: Эта статья является частью руководства по развертыванию BranchCache для Windows Server 2016, в котором показано, как развернуть BranchCache в распределенном и размещенном режимах кэша для оптимизации использования пропускной способности глобальной сети в филиалах.
manager: brianlic
ms.prod: windows-server
ms.technology: networking-bc
ms.topic: get-started-article
ms.assetid: a3f1f7c4-d9b2-43e6-8bfa-fac707bbd4d3
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 1e450b9a2282cb4820b8802aa6d36e822f56ca12
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71356591"
---
# <a name="enable-hash-publication-for-domain-member-file-servers"></a>Включение возможности публикации хэша для файловых серверов, входящих в домен

>Относится к: Windows Server (Semi-Annual Channel), Windows Server 2016

При использовании домен Active Directory Services (AD DS) можно использовать групповая политика домена, чтобы включить публикацию хэша BranchCache для нескольких файловых серверов. Для этого необходимо создать подразделение, добавить файловые серверы в подразделение, создать публикацию хэша BranchCache групповая политика объект (GPO), а затем настроить объект групповой политики.  
  
Сведения о включении публикации хэша для нескольких файловых серверов см. в следующих разделах.  
  
-   [Создание подразделения файловых серверов BranchCache](../../branchcache/deploy/Create-the-BranchCache-File-Servers-Organizational-Unit.md)  
  
-   [Перемещение файловых серверов в организационное подразделение файловых серверов BranchCache](../../branchcache/deploy/Move-File-Servers-to-the-BranchCache-File-Servers-Organizational-Unit.md)  
  
-   [Создание групповая политика объекта для публикации хэша BranchCache](../../branchcache/deploy/Create-the-BranchCache-Hash-Publication-Group-Policy-Object.md)  
  
-   [Настройка групповая политика объекта для публикации хэша BranchCache](../../branchcache/deploy/Configure-the-BranchCache-Hash-Publication-Group-Policy-Object.md)  
  


