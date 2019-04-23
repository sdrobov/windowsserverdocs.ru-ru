---
title: Перенос параметров и данных Windows SBS 2011 Essentials на целевой сервер для миграции Windows Server Essentials
description: Описывает способ использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 47548994-9fa0-42e0-afa4-c2ccbd063acb
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 80ef8a196f70a77e149dc8defaacf20a82d576e7
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59859325"
---
# <a name="move-windows-sbs-2011-essentials-settings-and-data-to-the-destination-server-for-windows-server-essentials-migration"></a>Перенос параметров и данных Windows SBS 2011 Essentials на целевой сервер для миграции Windows Server Essentials

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Перенесите параметры и данные на целевой сервер следующим образом:  
  

1.  [Копирование данных на конечный сервер](Move-Windows-SBS-2011-Essentials-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md#BKMK_CopyData)  
  
2.  [Импорт учетных записей пользователей Active Directory для панели мониторинга Windows Server Essentials (необязательно)](Move-Windows-SBS-2011-Essentials-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md#BKMK_ImportADaccounts)  
  
3.  [Настройка сети](Move-Windows-SBS-2011-Essentials-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md#BKMK_Network)  
  
4.  [Сопоставить разрешенные компьютеры с учетных записей пользователей](Move-Windows-SBS-2011-Essentials-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md#BKMK_MapPermittedComputers)  
 
##  <a name="BKMK_CopyData"></a> Копирование данных на конечный сервер  
 Перед копированием данных с исходного сервера на целевой сервер выполните следующие действия.  
  
-   Просмотрите список общих папок на исходном сервере, включая разрешения для каждой папки. Создайте или настройте папки на целевом сервере в соответствии со структурой папок, которую вы перемещаете с исходного сервера.  
  
-   Проверьте размер каждой папки и убедитесь, что целевой сервер имеет достаточно свободного места.  
  
-   Сделайте общие папки на исходном сервере доступными только для чтения для всех пользователей, чтобы при копировании файлов на целевой сервер операции записи не выполнялись и не занимали место на диске.  
  
#### <a name="to-copy-data-from-the-source-server-to-the-destination-server"></a>Копирование данных с исходного сервера на целевой сервер  
  
1.  Войдите на целевой сервер с правами администратора домена, а затем откройте окно командной строки.  
  
2.  В командной строке введите следующую команду и нажмите клавишу ВВОД:  
  
    `robocopy \\<SourceServerName> \<SharedSourceFolderName> \\<DestinationServerName> \<SharedDestinationFolderName> /E /B /COPY:DATSOU /LOG:C:\Copyresults.txt`  
  
     Где
     - \<SourceServerName\> имя исходного сервера
     - \<SharedSourceFolderName\> — имя общей папки на исходном сервере
     - \<DestinationServerName\> — это имя конечного сервера
     - \<SharedDestinationFolderName\> — общая папка на целевом сервере, в который будут копироваться данные.  
        
3.  Повторите предыдущую операцию для каждой общей папки, которую вы перемещаете с исходного сервера.  
  
##  <a name="BKMK_ImportADaccounts"></a> Импорт учетных записей пользователей Active Directory для панели мониторинга Windows Server Essentials (необязательно)  
 По умолчанию все учетные записи пользователей, созданные на исходном сервере, автоматически переносятся на панели мониторинга в Windows Server Essentials. Однако процесс автоматического переноса учетной записи пользователя Active Directory завершится сбоем, если все свойства не будут соответствовать требованиям миграции. Для импорта пользователей Active Directory можно использовать следующий командлет Windows PowerShell.  
  
#### <a name="to-import-an-active-directory-user-account-to-the-windows-server-essentials-dashboard"></a>Импорт учетной записи пользователя Active Directory на панель мониторинга Windows Server Essentials  
  
1.  Войдите на целевой сервер как администратор домена.  
  
2.  Откройте Windows PowerShell от имени администратора.  
  
3.  Запустите следующий командлет, где `[AD username]` — имя учетной записи пользователя Active Directory, которую требуется импортировать:  
  
     `Import-WssUser  SamAccountName [AD username]`  
  
##  <a name="BKMK_Network"></a> Настройка сети  
  
#### <a name="to-configure-the-network"></a>Для настройки сети  
  
1.  На целевом сервере откройте панель мониторинга.  
  
2.  На панели мониторинга на **начальной** странице щелкните **Настройка**, затем **Настройка повсеместного доступа**и установите флажок **Щелкните, чтобы настроить повсеместный доступ** .  
  
3.  Выполните инструкции в мастере для настройки маршрутизатора и доменных имен.  
  
 Если ваш маршрутизатор не поддерживает инфраструктуру UPnP, или если инфраструктура UPnP отключена, то рядом с именем маршрутизатора может появиться желтый значок предупреждения. Убедитесь, что открыты следующие порты, и что они будут направляться на IP-адрес целевого сервера.  
  
-   Порт 80: Веб-трафик HTTP  
  
-   Порт 443: Веб-трафик HTTPS  
  
##  <a name="BKMK_MapPermittedComputers"></a> Сопоставить разрешенные компьютеры с учетных записей пользователей  
 Каждая учетная запись пользователя, которая переносится из Windows Small Business Server 2011 Essentials, должна быть сопоставлена с одним или несколькими компьютерами.  
  
#### <a name="to-map-user-accounts-to-computers"></a>Сопоставление учетных записей и компьютеров  
  
1.  Откройте панель мониторинга Windows Server Essentials.  
  
2.  На панели навигации щелкните **Пользователи**.  
  
3.  В списке учетных записей пользователей щелкните правой кнопкой мыши учетную запись пользователя и нажмите кнопку **Просмотреть свойства учетной записи**.  
  
4.  Перейдите на вкладку **Повсеместный доступ** , а затем установите флажок **Разрешить удаленный веб-доступ и доступ к веб-приложениям служб**.  
  
5.  Выберите **Общие папки**, затем **Компьютеры**, затем **Ссылки главной страницы**и нажмите кнопку **Применить**.  
  
6.  Перейдите на вкладку **Доступ к компьютеру**, а затем щелкните имя компьютера, доступ к которому вы хотите разрешить.  
  
7.  Повторите шаги 3, 4, 5 и 6 для каждой учетной записи пользователя.  
  
> [!NOTE]
>  Конфигурацию клиентского компьютера изменять не нужно. Она настраивается автоматически.  
  
> [!NOTE]
>  По окончании процесса миграции, если при создании первой новой учетной записи пользователя на целевом сервере появится проблема, удалите добавленную учетную запись пользователя, а затем создайте ее снова.
