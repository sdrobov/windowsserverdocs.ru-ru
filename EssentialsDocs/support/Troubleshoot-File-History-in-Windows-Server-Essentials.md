---
title: Устранение неполадок с историей файлов в Windows Server Essentials
description: Описывает способ использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ed062945-27e9-4572-b1bb-6c8cf1b9c2f4
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 34442565b54b089064c1fa19317a24f591e44fda
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59868605"
---
# <a name="troubleshoot-file-history-in-windows-server-essentials"></a>Устранение неполадок с историей файлов в Windows Server Essentials

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials 
  
## <a name="troubleshoot-issues-with-user-file-history-backups"></a>Устранение неполадок с резервными копиями истории файлов  
 При управлении резервными копиями истории файлов для пользователя или компьютера, который был добавлен на сервер под управлением Windows Server Essentials, могут возникнуть следующие проблемы.  
  
### <a name="file-history-data-is-not-automatically-deleted"></a>Данные истории файлов не удаляются автоматически  
 Данные истории файлов могут не удаляться автоматически в следующих случаях.  
  
-   При удалении учетной записи пользователя, необходимо выбрать не удалить учетную запись пользователя s данные истории файлов и удалить данные вручную.  
  
-   Если при попытке удаления данных истории файлов эти данные уже используются другим процессом.  
  
 Чтобы устранить эту проблему, необходимо вручную удалить историю файлов, используя следующую процедуру.  
  
####  <a name="BKMK_manuallyDelete"></a> Чтобы вручную удалить резервные копии истории файлов для пользователя или компьютера  
  
1.  Войдите на сервер с правами администратора.  
  
2.  Запустите проводник от имени администратора.  
  
3.  Перейдите к папке резервных копий истории файлов. Расположение по умолчанию — C:\ServerFolders\File History Backups.  
  
4.  Удалите общую папку, в которой находится резервная копия истории файлов.  
  
    -   Чтобы удалить историю файлов для пользователя, удалите резервную дочернюю папку истории файлов с именем пользователя s.  
  
    -   Чтобы удалить историю файлов для компьютера, удалите резервную дочернюю папку истории файлов с именем компьютера. Например, если пользователь прекращено < MyComputer01\> после начал работать на новом ноутбуке < MyComputer02\>, следует удалить C:\ServerFolders\File History Backups\\< MyAccount\> \\ < MyComputer01\> после проверки с пользователем, что она перенесена, все файлы и папки на новый ноутбук и устраняет потребность в истории файлов в будущем.  
  
### <a name="cannot-apply-file-history-setting-to-a-new-user"></a>Не удается применить параметр истории файлов для нового пользователя  
 При добавлении нового пользователя, имя которого совпадает с именем пользователя, удаленного из Windows Server Essentials, конфигурирование истории файлов для нового пользователя может завершиться ошибкой из-за конфликта имен при попытке Windows Server Essentials создать папку для хранения истории файлов нового пользователя. Чтобы устранить эту проблему, переименуйте папку истории файлов для удаленного пользователя.  
  
##### <a name="to-locate-user-file-history-on-the-server"></a>Поиск истории файлов пользователя на сервере  
  
1.  Войдите на сервер с правами администратора.  
  
2.  На панели мониторинга Windows Server Essentials щелкните **Хранение**.  
  
3.  Запомните путь к папке резервных копий истории файлов с вкладки **Папки сервера**. Расположение по умолчанию — %SystemDrive%\ServerFolders\File History Backups\\.  
  
##### <a name="to-resolve-file-history-issues-for-a-new-user-with-a-name-conflict"></a>Решение проблем с историей файлов для новых пользователей с конфликтом имен  
  
1.  Войдите на сервер с правами администратора.  
  
2.  Запустите проводник от имени администратора.  
  
3.  Перейдите к папке резервных копий истории файлов. Расположение по умолчанию — C:\ServerFolders\File History Backups.  
  
     Папка резервных копий истории файлов содержит вложенную папку для каждой учетной записи пользователя, которая была добавлена в Windows Server Essentials. Например, история файлов для пользователя John Smith будет храниться во вложенной папке File History Backups\JohnSmith.  
  
4.  Переименуйте вложенную папку для пользователя, который вы удалили, например,  **< *UserName*> _Deleted**. Если история файлов пользователя больше не нужна, можно удалить эту папку.  
  

5.  Теперь можно добавить нового пользователя. Инструкции см. в разделе добавить учетную запись пользователя? в [управление учетными записями пользователей](../manage/Manage-User-Accounts-in-Windows-Server-Essentials.md).  
  
### <a name="a-user-account-was-removed-but-the-users-file-history-remains"></a>Учетная запись пользователя была удалена, но история файлов осталась  
 В некоторых случаях сетевой администратор может удалить пользователя или компьютер с сервера, но оставить резервную копию истории файлов для использования в будущем. Если история файлов больше не нужна, удалите папку резервных копий истории файлов для пользователя или компьютера из общих папок на сервере. Для этого см. [To manually delete File History backups for a user or a computer](Troubleshoot-File-History-in-Windows-Server-Essentials.md#BKMK_manuallyDelete).  

5.  Теперь можно добавить нового пользователя. Инструкции см. в разделе добавить учетную запись пользователя? в [управление учетными записями пользователей](../manage/Manage-User-Accounts-in-Windows-Server-Essentials.md).  
  
### <a name="a-user-account-was-removed-but-the-users-file-history-remains"></a>Учетная запись пользователя была удалена, но история файлов осталась  
 В некоторых случаях сетевой администратор может удалить пользователя или компьютер с сервера, но оставить резервную копию истории файлов для использования в будущем. Если история файлов больше не нужна, удалите папку резервных копий истории файлов для пользователя или компьютера из общих папок на сервере. Для этого см. [To manually delete File History backups for a user or a computer](../support/Troubleshoot-File-History-in-Windows-Server-Essentials.md#BKMK_manuallyDelete).  

  
## <a name="see-also"></a>См. также  
  
-   [Управление архивацией клиента](../manage/Manage-Client-Computer-Backup-in-Windows-Server-Essentials.md)  
  

-   [Поддержка Windows Server Essentials](Support-Windows-Server-Essentials.md)

-   [Поддержка Windows Server Essentials](../support/Support-Windows-Server-Essentials.md)

