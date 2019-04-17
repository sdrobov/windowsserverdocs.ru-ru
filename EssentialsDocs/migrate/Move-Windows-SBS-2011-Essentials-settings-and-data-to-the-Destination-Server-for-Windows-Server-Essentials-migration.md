---
title: "Перемещение данных и параметров Windows SBS 2011 Essentials на целевой сервер для миграции Windows Server Essentials"
description: "Описывается, как использовать Windows Server Essentials"
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
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="move-windows-sbs-2011-essentials-settings-and-data-to-the-destination-server-for-windows-server-essentials-migration"></a>Перемещение данных и параметров Windows SBS 2011 Essentials на целевой сервер для миграции Windows Server Essentials

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Перенос параметров и данных на целевой сервер следующим образом:  
  

1.  [Копирование данных на конечный сервер](Move-Windows-SBS-2011-Essentials-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md#BKMK_CopyData)  
  
2.  [Импорт пользовательских учетных записей Active Directory для мониторинга Windows Server Essentials (необязательно)](Move-Windows-SBS-2011-Essentials-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md#BKMK_ImportADaccounts)  
  
3.  [Настройка сети](Move-Windows-SBS-2011-Essentials-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md#BKMK_Network)  
  
4.  [Сопоставление разрешенных компьютеров с учетными записями пользователей](Move-Windows-SBS-2011-Essentials-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md#BKMK_MapPermittedComputers)  
 
##  <a name="BKMK_CopyData"></a>Копирование данных на конечный сервер  
 Перед копированием данных с исходного сервера на конечный сервер, выполните следующие задачи.  
  
-   Просмотрите список общих папок на исходном сервере, включая разрешения для каждой папки. Создайте или настройте папки на конечном сервере в соответствии со структурой папок, которую вы перемещаете с исходного сервера.  
  
-   Проверьте размер каждой папки и убедитесь, что целевой сервер имеет достаточно свободного дискового пространства.  
  
-   Сделайте общие папки на исходном сервере только для чтения для всех пользователей, не записи может занять место на диске, при копировании файлов на конечный сервер.  
  
#### <a name="to-copy-data-from-the-source-server-to-the-destination-server"></a>Копирование данных с исходного сервера на конечный сервер  
  
1.  Войдите на конечный сервер с правами администратора домена и откройте окно командной строки.  
  
2.  В командной строке введите следующую команду и нажмите клавишу ВВОД:  
  
    `robocopy \\<SourceServerName> \<SharedSourceFolderName> \\<DestinationServerName> \<SharedDestinationFolderName> /E /B /COPY:DATSOU /LOG:C:\Copyresults.txt`  
  
     Где:
     - \ < SourceServerName\ > — имя исходного сервера
     - \ < SharedSourceFolderName\ > — имя общей папки на исходном сервере
     - \ < DestinationServerName\ > — имя конечного сервера
     - \ < SharedDestinationFolderName\ > — Общая папка на конечном сервере, на который будут копироваться данные.  
        
3.  Повторите предыдущий шаг для каждой общей папки, которую вы перемещаете с исходного сервера.  
  
##  <a name="BKMK_ImportADaccounts"></a>Импорт пользовательских учетных записей Active Directory для мониторинга Windows Server Essentials (необязательно)  
 По умолчанию все учетные записи пользователей, созданные на исходном сервере, автоматически переносятся на панель мониторинга в Windows Server Essentials. Тем не менее автоматического переноса учетной записи пользователя в Active Directory завершится сбоем, если все свойства не будут соответствовать требованиям миграции. Следующий командлет Windows PowerShell можно использовать для импорта пользователей Active Directory.  
  
#### <a name="to-import-an-active-directory-user-account-to-the-windows-server-essentials-dashboard"></a>Чтобы импортировать учетную запись пользователя Active Directory на панели мониторинга Windows Server Essentials  
  
1.  Войдите на целевой сервер как администратор домена.  
  
2.  Откройте Windows PowerShell от имени администратора.  
  
3.  Выполните следующий командлет, где `[AD username]` — это имя учетной записи пользователя Active Directory, который требуется импортировать:  
  
     `Import-WssUser  SamAccountName [AD username]`  
  
##  <a name="BKMK_Network"></a>Настройка сети  
  
#### <a name="to-configure-the-network"></a>Для настройки сети  
  
1.  На конечном сервере откройте панель мониторинга.  
  
2.  На панели мониторинга **Главная** щелкните **установки**, нажмите кнопку **Настройка повсеместного доступа**и выберите **щелкните, чтобы настроить Повсеместный доступ** параметр.  
  
3.  Выполните инструкции в мастере для настройки маршрутизатора и доменных имен.  
  
 Если маршрутизатор не поддерживает инфраструктуру UPnP, или если UPnP-инфраструктура отключена, рядом с именем маршрутизатора может появиться желтый значок предупреждения. Убедитесь, что открыты следующие порты, и что они будут направляться на IP-адрес конечного сервера:  
  
-   Порт 80: Веб-трафик HTTP  
  
-   Порт 443: Веб-трафик HTTPS  
  
##  <a name="BKMK_MapPermittedComputers"></a>Сопоставление разрешенных компьютеров с учетными записями пользователей  
 Каждая учетная запись пользователя, которая переносится из Windows Small Business Server 2011 Essentials должна быть сопоставлена с одним или несколькими компьютерами.  
  
#### <a name="to-map-user-accounts-to-computers"></a>Сопоставление учетных записей и компьютеров  
  
1.  Откройте панель мониторинга Windows Server Essentials.  
  
2.  На панели навигации щелкните **пользователей**.  
  
3.  В списке учетных записей пользователей, щелкните правой кнопкой мыши учетную запись пользователя и нажмите кнопку **просмотреть свойства учетной записи**.  
  
4.  Нажмите кнопку **повсеместного доступа** , а затем щелкните **разрешить удаленный веб-доступ и доступ к веб-приложениям служб**.  
  
5.  Выберите **общих папок**, выберите **компьютеры**выберите **ссылки главной страницы**, а затем нажмите кнопку **применить**.  
  
6.  Нажмите кнопку **доступ к компьютеру** , а затем щелкните имя компьютера, к которому вы хотите разрешить доступ.  
  
7.  Повторите шаги 3, 4, 5 и 6 для каждой учетной записи пользователя.  
  
> [!NOTE]
>  Необходимо изменить конфигурацию клиентского компьютера. Она настраивается автоматически.  
  
> [!NOTE]
>  По окончании процесса миграции, если вы столкнулись с проблемой при создании первой новой учетной записи пользователя на конечном сервере, удалить учетную запись пользователя, который вы добавили и создайте его заново.
