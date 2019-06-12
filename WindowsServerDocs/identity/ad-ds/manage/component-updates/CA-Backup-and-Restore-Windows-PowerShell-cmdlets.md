---
ms.assetid: 7e195f5b-b194-40f3-a26d-5cf4ade5fc4d
title: Командлеты резервного копирования ЦС и восстановление Windows PowerShell
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 6055d9b694f72a6a874acdcb5135fde61bcf0d76
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66442748"
---
# <a name="ca-backup-and-restore-windows-powershell-cmdlets"></a>Командлеты резервного копирования ЦС и восстановление Windows PowerShell

> Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012
> 
> **Автор**: Джастин Тернер, старший инженер по улучшению поддержки с группой Windows  
> 
> [!NOTE]
> Этот материал создан инженером службы поддержки клиентов Майкрософт и предназначен для опытных администраторов и архитекторов систем, которым нужны более глубокие технические сведения о функциях и решениях в Windows Server 2012 R2, а не обычная информация, доступная в статьях на сайте TechNet. Однако он не был отредактирован согласно требованиям сайта, поэтому некоторые формулировки могут быть не такими выверенными, как на станицах TechNet.  
  
## <a name="overview"></a>Обзор  
Модуль ADCSAdministration Windows PowerShell впервые появился в Windows Server 2012.  Этот модуль в Window Server 2012 R2 для поддержки резервного копирования и восстановления ЦС были добавлены два новых командлета.  
  
-   Backup-CARoleService  
  
-   Restore-CARoleService  
  
## <a name="backup-caroleservice"></a>Backup-CARoleService  
**Таблицы SEQ таблицы \\ \* ARABIC 17: Резервное копирование и восстановление Windows PowerShell командлеты**  
  
**ADCSAdministration командлета: BACKUP-CARoleService**  
  
|Аргументы - **Полужирный** аргументы являются обязательными|Описание|  
|------------------------------------------------|---------------|  
|**-Path**|-Строка — место для сохранения резервной копии<br />— Это единственное неименованными параметрами<br />-позиционных параметров<br /><br />**Пример:**<br /><br />BACKUP-CARoleService.-путь c:\adcsbackup1<br /><br />BACKUP-CARoleService c:\adcsbackup2|  
|-KeyOnly|-Создать резервную копию сертификата ЦС без базы данных<br /><br />**Пример:**<br /><br />BACKUP-CARoleService c:\adcsbackup3 - KeyOnly|  
|-Password|— Указывает пароль для защиты ЦС сертификатов и закрытых ключей<br />— Должен быть защищенной строкой<br />-Не является допустимым параметром - DatabaseOnly<br /><br />Пример.<br /><br />BACKUP-CARoleService c:\adcsbackup4-пароль (Read-Host - строка «пароль:» - AsSecureString)<br /><br />BACKUP-CARoleService c:\adcsbackup5-пароль (ConvertTo-SecureString «Pa55w0rd!» -AsPlainText -Force)|  
|-DatabaseOnly|— Резервное копирование базы данных без сертификата ЦС<br /><br />BACKUP-CARoleService c:\adcsbackup6 - DatabaseOnly|  
|-Force|1.  Позволяет перезаписать резервную копию, осуществления в расположении, указанном в параметре - Path<br /><br />BACKUP-CARoleService c:\adcsbackup1-Force|  
|-Добавочное|-Выполнить добавочную архивацию<br /><br />BACKUP-CARoleService c:\adcsbackup7-добавочное|  
|-KeepLog|1.  Указывает команду, чтобы сохранить файлы журнала. Если параметр не указан, файлы журналов обрезаются по умолчанию, за исключением добавочных сценария<br /><br />BACKUP-CARoleService c:\adcsbackup7 - KeepLog|  
  
### <a name="-password-secure-string"></a>-Password <Secure String>  
Если - пароль используется параметр, введенный пароль должен быть защищенной строкой.  Используйте **Read-Host** командлет, чтобы запустить интерактивное приглашение для ввода пароля для безопасного, либо использовать **ConvertTo-SecureString** , чтобы указать пароль в строке.  
  
Изучите приведенные ниже примеры  
  
**Указание защищенной строки в параметре пароль, с помощью Read-Host**  
  
```powershell  
Backup-CARoleService c:\adcsbackup4 -Password (Read-Host -prompt "Password:" -AsSecureString)  
```  
  
**Указание защищенной строки в параметре пароль, с помощью ConvertTo-SecureString**  
  
```powershell  
Backup-CARoleService c:\adcsbackup5 -Password (ConvertTo-SecureString "Pa55w0rd!" -AsPlainText -Force)  
```  
  
## <a name="restore-caroleservice"></a>Restore-CARoleService  
**ADCSAdministration командлета: RESTORE-CARoleService**  
  
|Аргументы - **Полужирный** аргументы являются обязательными|Описание|  
|------------------------------------------------|---------------|  
|**-Path**|-Строка — расположение для восстановления из резервной копии<br />— Это единственное неименованными параметрами<br />-позиционных параметров<br /><br />**Пример:**<br /><br />RESTORE-CARoleService.-путь c:\adcsbackup1-Force<br /><br />RESTORE-CARoleService c:\adcsbackup2-Force|  
|-KeyOnly|— Восстановление сертификата ЦС без базы данных<br />— Должен быть указан, если резервной копии с параметром - KeyOnly<br /><br />**Пример:**<br /><br />RESTORE-CARoleService c:\adcsbackup3 - KeyOnly-Force|  
|-Password|— Указывает пароль для сертификатов ЦС и закрытого ключей<br />— Должен быть защищенной строкой<br /><br />**Пример:**<br /><br />RESTORE-CARoleService c:\adcsbackup4-пароль (read-host - строка «пароль:» - AsSecureString)-Force<br /><br />RESTORE-CARoleService c:\adcsbackup5-пароль (ConvertTo-SecureString «Pa55w0rd!» -AsPlainText -Force) -Force|  
|-DatabaseOnly|-Восстановление базы данных без сертификата ЦС<br /><br />RESTORE-CARoleService c:\adcsbackup6 - DatabaseOnly|  
|-Force|-Позволяет перезаписать существующие ранее ключи<br />— Это необязательный параметр, но при восстановлении на месте, это скорее всего требуется<br /><br />RESTORE-CARoleService c:\adcsbackup1-Force|  
  
### <a name="issues"></a>Проблемы  
Без использования пароля защищенного резервного копирования, если функция ConvertTo-SecureString завершается с ошибкой при использовании Backup-CARoleService с помощью параметра - пароль.  
  
![ЦС резервного копирования и восстановления](media/CA-Backup-and-Restore-Windows-PowerShell-cmdlets/GTR_ADDS_BackupCARole.gif)  
  
**Таблицы SEQ таблицы \\ \* ARABIC 18: Распространенные ошибки**  
  
|Действие|Ошибка|Примечание|  
|----------|---------|-----------|  
|**RESTORE-CARoleService C:\ADCSBackup**|RESTORE-CARoleService: Процесс нет доступа к файлу, так как он используется другим процессом. (Исключение из HRESULT:<br /><br />0x80070020)|Остановка службы служб сертификатов Active Directory перед запуском командлета Restore-CARoleService|  
|**RESTORE-CARoleService C:\ADCSBackup**|RESTORE-CARoleService: Каталог не пуст. (Исключение из HRESULT: 0x80070091)|Используйте параметр - Force для перезаписи существующих ключей|  
|**BACKUP-CARoleService C:\ADCSBackup-пароль (Read-Host - Prompt «пароль:» - AsSecureString) - DatabaseOnly**|BACKUP-CARoleService: Набор параметров невозможно разрешить с помощью указанного именованные параметры.|-Пароль параметр используется только для пароля защищают закрытые ключи и поэтому является недопустимым, если их не при резервном копировании|  
|**Restore-CARoleService C:\ADCSBack15 -Password (Read-Host -Prompt "Password:" -AsSecureString) -DatabaseOnly**|RESTORE-CARoleService: Набор параметров невозможно разрешить с помощью указанного именованные параметры.|-Пароль параметр используется только для пароля защищают закрытые ключи и поэтому является недопустимым, если вы восстанавливаете не их|  
|**Restore-CARoleService C:\ADCSBack14 -Password (Read-Host -Prompt "Password:" -AsSecureString)**|RESTORE-CARoleService: Системе не удается найти указанный файл. (Исключение из HRESULT: 0x80070002)|Указанный путь не содержит допустимой базой данных резервной копии.  Возможно, путь является недопустимым или создания резервной копии с параметром - KeysOnly?|  
  
## <a name="additional-resources"></a>Дополнительные ресурсы  
[Руководство по миграции служб сертификации Active Directory](https://technet.microsoft.com/library/ee126170(v=ws.10).aspx)  
  
[Резервное копирование базы данных и закрытого ключа ЦС](https://technet.microsoft.com/library/ee126140(v=ws.10).aspx#BKMK_BackUpDB)  
  
[Восстановление базы данных и конфигурации ЦС на сервере назначения](https://technet.microsoft.com/library/ee126140(v=ws.10).aspx#BKMK_RestoreCA)  
  
## <a name="try-this-backup-the-ca-in-your-lab-using-windows-powershell"></a>Попробуйте выполните следующее: Резервное копирование ЦС в лаборатории с помощью Windows PowerShell  
  
1.  Используйте команды на этом занятии, чтобы создать резервную копию базы данных ЦС и закрытый ключ защищен паролем.  
  
2.  Воздержаться от восстановления ЦС в данный момент.  
  


