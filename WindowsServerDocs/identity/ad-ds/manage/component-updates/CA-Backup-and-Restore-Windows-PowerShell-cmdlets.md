---
ms.assetid: 7e195f5b-b194-40f3-a26d-5cf4ade5fc4d
title: "Резервное копирование ЦС и восстановить командлеты Windows PowerShell"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: aba86ed080cc0b4043805531f0a2138b1b1d3cf8
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="ca-backup-and-restore-windows-powershell-cmdlets"></a>Резервное копирование ЦС и восстановить командлеты Windows PowerShell

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012
>
**Автор**: Джастин Тернер, старший инженер по улучшению поддержки с группой Windows  
  
> [!NOTE]  
> Этот материал создан инженером поддержки клиентов Майкрософт и предназначен для опытных администраторов и архитекторов систем, которым нужны более глубокие технические сведения о функциях и решениях в Windows Server 2012 R2, чем обычно предоставляют разделов на TechNet. Однако он не проходил же редактирования этапах, поэтому некоторые формулировки могут быть то, что обычно станицах на сайте TechNet.  
  
## <a name="overview"></a>Обзор  
Модуль ADCSAdministration Windows PowerShell впервые появился в окне Server 2012.  Этот модуль в окне Server 2012 R2 для поддержки резервного копирования и восстановления ЦС были добавлены два новых командлета.  
  
-   Backup-CARoleService  
  
-   Restore-CARoleService  
  
## <a name="backup-caroleservice"></a>Backup-CARoleService  
**Таблица SEQ Table \\\ * ARABIC 17: резервное копирование и восстановление командлеты Windows PowerShell**  
  
**Командлет ADCSAdministration: Backup-CARoleService**  
  
|Аргументы - **Полужирный** аргументы требуются|Описание|  
|------------------------------------------------|---------------|  
|**-Path**|-String — расположение для сохранения резервной копии<br />— Это единственный безымянного параметра<br />-позиционный параметр<br /><br />**Пример:**<br /><br />Backup-CARoleService.-c:\adcsbackup1 путь<br /><br />C:\adcsbackup2 Backup-CARoleService|  
|-KeyOnly|-Резервное копирование сертификата ЦС без базы данных<br /><br />**Пример:**<br /><br />Backup-CARoleService c:\adcsbackup3 - KeyOnly|  
|-Пароль|— Задает пароль для защиты ЦС сертификатов и закрытых ключей<br />-Должно быть защищенной строкой<br />-Не действителен с помощью параметра - DatabaseOnly<br /><br />Пример:<br /><br />C:\adcsbackup4 Backup-CARoleService-пароль (Read-Host-запрос «пароль:» - AsSecureString)<br /><br />C:\adcsbackup5 Backup-CARoleService-пароль (ConvertTo-SecureString «Pa55w0rd!» -AsPlainText - Force)|  
|-DatabaseOnly|-Резервное копирование базы данных без сертификата ЦС<br /><br />Backup-CARoleService c:\adcsbackup6 - DatabaseOnly|  
|-Force|1. позволяет перезаписать резервную копию, которая уже существует в расположении, заданном параметром - Path<br /><br />C:\adcsbackup1 Backup-CARoleService-Force|  
|-Добавочное|-Выполнить добавочную архивацию<br /><br />C:\adcsbackup7 Backup-CARoleService-добавочное|  
|-KeepLog|1. указывает, что команды, чтобы сохранить файлы журнала. Если параметр не указан, по умолчанию, за исключением в сценарии добавочные происходит усечение файлов журнала<br /><br />Backup-CARoleService c:\adcsbackup7 - KeepLog|  
  
### <a name="-password-secure-string"></a>-Пароль <Secure String>  
Если - пароль используется параметр, указанный пароль должен быть защищенной строкой.  Используйте **Read-Host** командлету запустите интерактивную командную строку для записи безопасного пароля или использовать **ConvertTo-SecureString** командлет, чтобы указать пароль в строке.  
  
Просмотрите следующие примеры  
  
**Указание защищенной строки для параметра пароль, с помощью Read-Host**  
  
```powershell  
Backup-CARoleService c:\adcsbackup4 -Password (Read-Host -prompt "Password:" -AsSecureString)  
```  
  
**Указание защищенной строки для параметра пароль, с помощью ConvertTo-SecureString**  
  
```powershell  
Backup-CARoleService c:\adcsbackup5 -Password (ConvertTo-SecureString "Pa55w0rd!" -AsPlainText -Force)  
```  
  
## <a name="restore-caroleservice"></a>Restore-CARoleService  
**Командлет ADCSAdministration: Restore-CARoleService**  
  
|Аргументы - **Полужирный** аргументы требуются|Описание|  
|------------------------------------------------|---------------|  
|**-Path**|-String — расположение для восстановления резервной копии из<br />— Это единственный безымянного параметра<br />-позиционный параметр<br /><br />**Пример:**<br /><br />Restore-CARoleService. - путь c:\adcsbackup1 - Force<br /><br />C:\adcsbackup2 Restore-CARoleService-Force|  
|-KeyOnly|-Восстановить сертификат ЦС без базы данных<br />-Необходимо указать, если резервной копии с помощью параметра - KeyOnly<br /><br />**Пример:**<br /><br />Restore-CARoleService c:\adcsbackup3 - KeyOnly-Force|  
|-Пароль|-Пароль, сертификаты и закрытые ключи<br />-Должно быть защищенной строкой<br /><br />**Пример:**<br /><br />C:\adcsbackup4 Restore-CARoleService-пароль (чтение host - строки «пароль:» - AsSecureString)-Force<br /><br />C:\adcsbackup5 Restore-CARoleService-пароль (ConvertTo-SecureString «Pa55w0rd!» -AsPlainText - Force)-Force|  
|-DatabaseOnly|-Восстановить базу данных без сертификата ЦС<br /><br />Restore-CARoleService c:\adcsbackup6 - DatabaseOnly|  
|-Force|— Позволяет перезаписать существующие ключи<br />-— Необязательный параметр, но при восстановлении на месте, она необходима вероятность<br /><br />C:\adcsbackup1 Restore-CARoleService-Force|  
  
### <a name="issues"></a>Проблемы  
Без использования пароля защищенных резервная копия, если происходит сбой функции ConvertTo-SecureString при использовании Backup-CARoleService с помощью параметра - пароль.  
  
![ЦС резервного копирования и восстановления](media/CA-Backup-and-Restore-Windows-PowerShell-cmdlets/GTR_ADDS_BackupCARole.gif)  
  
**Таблица SEQ Table \\\ * ARABIC 18: распространенных ошибок**  
  
|Действие|Ошибка|Комментарий|  
|----------|---------|-----------|  
|**Restore-CARoleService C:\ADCSBackup**|Restore-CARoleService: процесс нет доступа к файлу, так как он используется другим процессом. (Исключение из HRESULT:<br /><br />0x80070020)|Остановите службы сертификатов Active Directory перед запуском командлета Restore-CARoleService|  
|**Restore-CARoleService C:\ADCSBackup**|Restore-CARoleService: каталог не пуст. (Исключение из HRESULT: 0x80070091)|Используйте параметр - Force для перезаписи ранее существовавшие ключей|  
|**Backup-CARoleService C:\ADCSBackup-пароль (Read-Host-Prompt «пароль:» - AsSecureString) - DatabaseOnly**|Backup-CARoleService: набор параметров не удается разрешить с помощью указанных именованных параметров.|-Пароль параметр используются только для пароля защиты закрытых ключей и поэтому является недопустимым, когда их не резервное копирование|  
|**Restore-CARoleService C:\ADCSBack15-пароль (Read-Host-Prompt «пароль:» - AsSecureString) - DatabaseOnly**|Restore-CARoleService: набор параметров не удается разрешить с помощью указанных именованных параметров.|-Пароль параметр используются только для пароля защиты закрытых ключей и поэтому является недопустимым, когда их не восстановления|  
|**Restore-CARoleService C:\ADCSBack14-пароль (Read-Host-Prompt «пароль:» - AsSecureString)**|Restore-CARoleService: системе не удается найти указанный файл. (Исключение из HRESULT: 0x80070002)|Указанный путь не содержит резервной копии базы данных.  Возможно, путь является недопустимым или резервной копии с помощью параметра - KeysOnly?|  
  
## <a name="additional-resources"></a>Дополнительные ресурсы  
[Руководство по миграции служб сертификации Active Directory](https://technet.microsoft.com/library/ee126170(v=ws.10).aspx)  
  
[Резервное копирование базы данных ЦС и закрытого ключа](https://technet.microsoft.com/library/ee126140(v=ws.10).aspx#BKMK_BackUpDB)  
  
[Восстановление базы данных ЦС и конфигурации на конечном сервере](https://technet.microsoft.com/library/ee126140(v=ws.10).aspx#BKMK_RestoreCA)  
  
## <a name="try-this-backup-the-ca-in-your-lab-using-windows-powershell"></a>Выполните следующие действия: Резервное копирование ЦС в лаборатории с помощью Windows PowerShell  
  
1.  Резервное копирование базы данных ЦС и закрытый ключ защищен паролем, используйте команды в этом разделе.  
  
2.  Отложить обновление на восстановление ЦС в данный момент.  
  


