---
title: "Шаг 7: Выполнение задач после миграции для миграции Windows Server Essentials"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d382e3fd-d393-4bd0-883f-db50104a969f
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 6a61d28f29097bcb6993a471587f4cc1ae0bcc3f
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="step-7-perform-post-migration-tasks-for-the-windows-server-essentials-migration"></a>Шаг 7: Выполнение задач после миграции для миграции Windows Server Essentials

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Следующие задачи помогут вам завершить настройку конечного сервера с теми же параметрами, которые были на исходном сервере. Вы может отключили некоторые из этих параметров на исходном сервере во время процесса миграции, поэтому они не были перенесены на конечный сервер.  
  
1.  [Удаление записей DNS для исходного сервера](Step-7--Perform-post-migration-tasks-for-the-Windows-Server-Essentials-migration.md#BKMK_DeleteDNSEntries)  
  
2.  [Общий доступ к бизнес- и другие папки для данных приложения](Step-7--Perform-post-migration-tasks-for-the-Windows-Server-Essentials-migration.md#BKMK_ShareLineOfBusinessAndOtherApplications)  
  
##  <a name="BKMK_DeleteDNSEntries"></a>Удаление записей DNS для исходного сервера  
 После списания исходного сервера, сервера службы доменных имен (DNS) может все еще содержать элементы, указывающие на исходном сервере. Удалите эти записи DNS.  
  
#### <a name="to-delete-dns-entries-that-point-to-the-source-server"></a>Чтобы удалить DNS-записи, указывающие на исходном сервере  
  
1.  На конечном сервере откройте **диспетчера DNS**.  
  
2.  В диспетчере DNS щелкните правой кнопкой мыши имя сервера, нажмите кнопку **свойства**, а затем нажмите кнопку **серверов пересылки** вкладку.  
  
3.  Определите, есть ли запись в список серверов пересылки, указывающую на исходном сервере. Если существует, щелкните **изменить**и затем удалите эту запись в **редактировать пересылки** окна.  
  
4.  В **диспетчера DNS**, разверните имя сервера, а затем разверните **зоны прямого просмотра**.  
  
5.  Для каждой зоны прямого просмотра щелкните правой кнопкой мыши зону, нажмите кнопку **свойства**, а затем нажмите кнопку **серверы имен** вкладку.  
  
6.  Выберите запись в **серверов имен** текстовое поле, которое указывает на исходный сервер, щелкните **удалить**, а затем нажмите кнопку **ОК**.  
  
7.  Повторите шаги 5 и 6, пока не будут удалены все указатели на исходный сервер.  
  
8.  Нажмите кнопку **ОК** закрыть **свойства** окна.  
  
9. В **диспетчера DNS**, разверните **зоны обратного просмотра**.  
  
10. Повторите шаги 6 – 9, чтобы удалить все зоны обратного просмотра, которые указывают на исходном сервере.  
  
##  <a name="BKMK_ShareLineOfBusinessAndOtherApplications"></a>Общий доступ к бизнес- и другие папки для данных приложения  
 Необходимо задать разрешения для общей папки и разрешения NTFS для строки бизнеса и другие папки для данных приложения, скопированных на конечный сервер. После настройки разрешений общие папки отображаются на панели мониторинга на **хранилища** вкладку.  
  
 Если вы используете сценарий входа для сопоставления дисков с общими папками, для сопоставления с дисками на конечном сервере сценарий необходимо обновить.  
  
## <a name="next-steps"></a>Дальнейшие действия  
 Вы выполнили задачи после миграции для миграции Windows Server Essentials. Теперь перейдите к [шаг 8 — запуска Windows Server Essentials Best Practices Analyzer](Step-8--Run-the-Windows-Server-Essentials-Best-Practices-Analyzer.md).  
  

Для просмотра всех шагов см [переход на Windows Server Essentials](Migrate-from-Previous-Versions-to-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md).

