---
title: Шаг 7. Выполнение задач после миграции для миграции Windows Server Essentials
description: Описывает способ использования Windows Server Essentials
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
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59819165"
---
# <a name="step-7-perform-post-migration-tasks-for-the-windows-server-essentials-migration"></a>Шаг 7. Выполнение задач после миграции для миграции Windows Server Essentials

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Следующие задачи помогут вам завершить настройку конечного сервера с теми же параметрами, которые были на исходном сервере. Возможно, вы отключили некоторые из этих параметров на исходном сервере во время процесса миграции, поэтому они не были перенесены на конечный сервер.  
  
1.  [Удалите записи DNS для исходного сервера](Step-7--Perform-post-migration-tasks-for-the-Windows-Server-Essentials-migration.md#BKMK_DeleteDNSEntries)  
  
2.  [Совместное использование бизнес- и другим папкам данных приложения](Step-7--Perform-post-migration-tasks-for-the-Windows-Server-Essentials-migration.md#BKMK_ShareLineOfBusinessAndOtherApplications)  
  
##  <a name="BKMK_DeleteDNSEntries"></a> Удалите записи DNS для исходного сервера  
 После списания исходного сервера, сервера сервер службы доменных имен (DNS) может все еще содержать элементы, указывающие на этот исходный сервер. Удалите эти записи DNS.  
  
#### <a name="to-delete-dns-entries-that-point-to-the-source-server"></a>Чтобы удалить DNS-записи, которые ссылаются на исходный сервер  
  
1.  Откройте **Диспетчер DNS**на конечном сервере .  
  
2.  В диспетчере DNS щелкните правой кнопкой мыши имя сервера, щелкните **Свойства**, а затем перейдите на вкладку **Серверы пересылки** .  
  
3.  Определите, имеется ли в списке пересылок запись, указывающая на исходный сервер. Если такая запись есть, нажмите кнопку **Изменить** и удалите эту запись в окне **Редактировать серверы пересылки**.  
  
4.  В окне **Диспетчер DNS** разверните имя сервера и затем разверните пункт **Зоны прямого просмотра**.  
  
5.  Для каждой зоны прямого просмотра щелкните правой кнопкой мыши зону, выберите пункт **Свойства**, а затем откройте вкладку **Серверы имен**.  
  
6.  Выберите запись в текстовом поле **Серверы имен**, которая указывает на исходный сервер, нажмите **Удалить**, а затем нажмите **ОК**.  
  
7.  Повторите шаги 5 и 6, пока не будут удалены все указатели на исходный сервер.  
  
8.  Нажмите кнопку **ОК**, чтобы закрыть окно **Свойства**.  
  
9. В окне **Диспетчер DNS**разверните пункт **Зоны обратного просмотра**.  
  
10. Повторите шаги 6–9, чтобы удалить все зоны обратного просмотра, которые указывают на исходный сервер.  
  
##  <a name="BKMK_ShareLineOfBusinessAndOtherApplications"></a> Совместное использование бизнес- и другим папкам данных приложения  
 Для скопированных на конечный сервер папок с данными бизнес-приложений и прочих приложений необходимо задать разрешения для общей папки и разрешения NTFS. После настройки разрешений общие папки отображаются на панели мониторинга на вкладке **Хранилище** .  
  
 Если для сопоставления дисков с общими папками вы используете сценарий входа, для сопоставления с дисками на конечном сервере сценарий необходимо обновить.  
  
## <a name="next-steps"></a>Следующие шаги  
 Вы выполнили задачи после миграции для миграции Windows Server Essentials. Теперь перейдите к [шаг 8 — запуск Windows Server Essentials Best Practices Analyzer](Step-8--Run-the-Windows-Server-Essentials-Best-Practices-Analyzer.md).  
  

Чтобы просмотреть все действия, см. в разделе [миграции на Windows Server Essentials](Migrate-from-Previous-Versions-to-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md).

