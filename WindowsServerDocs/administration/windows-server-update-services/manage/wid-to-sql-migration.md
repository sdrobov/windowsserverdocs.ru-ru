---
title: Миграция базы данных WSUS (внутренней базы данных Windows) внутренней базы данных Windows для SQL
description: Раздел службы Windows Server Update Service (WSUS) — как перенести базу данных WSUS (SUSDB) экземпляр внутренней базы данных Windows к локальному или удаленному экземпляру SQL Server.
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-wsus
ms.tgt_pltfrm: na
ms.topic: get-started article
ms.assetid: 90e3464c-49d8-4861-96db-ee6f8a09g7dr
author: coreyp-at-msft
ms.author: coreyp
manager: dougkim
ms.date: 07/25/2018
ms.openlocfilehash: 9015bbc54a4c4bda0f691b79dbb7d3ba8ddbc4a1
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66439892"
---
>Относится к: Windows Server 2012, Windows Server 2012 R2, Windows Server 2016

# <a name="migrating-the-wsus-database-from-wid-to-sql"></a>Миграция базы данных WSUS с внутренней базы данных Windows для SQL

Следуйте инструкциям ниже для переноса базы данных WSUS (SUSDB) из экземпляра внутренней базы данных Windows к локальному или удаленному экземпляру SQL Server.

## <a name="prerequisites"></a>предварительные требования

- Экземпляр SQL. Это может быть значение по умолчанию **MSSQLServer** или пользовательского экземпляра.
- SQL Server Management Studio
- WSUS с установленной ролью WID
- Службы IIS (это обычно включаются при установке WSUS с помощью диспетчера серверов). Он не установлен, его необходимо будет.

## <a name="migrating-the-wsus-database"></a>Миграция базы данных WSUS

### <a name="stop-the-iis-and-wsus-services-on-the-wsus-server"></a>Остановите службы IIS и службы WSUS на сервере WSUS

С помощью PowerShell (с повышенными правами) выполните следующую команду:

```powershell
    Stop-Service IISADMIN
    Stop-Service WsusService
```

### <a name="detach-susdb-from-the-windows-internal-database"></a>Отсоединение SUSDB из внутренней базы данных Windows

#### <a name="using-sql-management-studio"></a>С помощью SQL Management Studio

1. Щелкните правой кнопкой мыши **SUSDB** - &gt; **задачи** - &gt; щелкните **отсоединения**: ![изображение 1](images/image1.png)
2. Проверьте **удалить существующие соединения** и нажмите кнопку **ОК** (необязательно, если активных соединениях).
    ![изображение2](images/image2.png)

#### <a name="using-command-prompt"></a>Использование командной строки

> [!IMPORTANT]
> Ниже показано, как отсоединить базу данных WSUS (SUSDB) из экземпляра внутренней базы данных Windows с помощью **sqlcmd** служебной программы. Дополнительные сведения о **sqlcmd** служебной программы, см. в разделе [служебная программа sqlcmd](https://go.microsoft.com/fwlink/?LinkId=81183).
> 1. Откройте командную строку с повышенными правами
> 2. Выполните следующую команду SQL для отсоединения базы данных WSUS (SUSDB) из экземпляра внутренней базы данных Windows с помощью **sqlcmd** служебной программы:

```batchfile
        sqlcmd -S \\.\pipe\Microsoft##WID\tsql\query
        use master
        GO
        alter database SUSDB set single_user with rollback immediate
        GO
        sp_detach_db SUSDB
        GO
```

### <a name="copy-the-susdb-files-to-the-sql-server"></a>Скопируйте файлы SUSDB SQL Server

1. Копировать **файлы SUSDB.mdf** и **SUSDB\_log.ldf** из папки данных WID ( **% SystemDrive %** \** Windows\WID\Data **) к данным экземпляра SQL Папка.

> [!TIP]
> Например, если папка экземпляра SQL **C:\Program Files\Microsoft SQL Server\MSSQL12. MSSQLSERVER\MSSQL**, и к папке данных WID **C:\Windows\WID\Data,** скопируйте файлы SUSDB из **C:\Windows\WID\Data** для **C:\Program Files\Microsoft SQL Server \MSSQL12. MSSQLSERVER\MSSQL\Data**

### <a name="attach-susdb-to-the-sql-instance"></a>Присоедините SUSDB к экземпляру SQL

1. В **SQL Server Management Studio**в разделе **экземпляр** узел, щелкните правой кнопкой мыши **баз данных**, а затем нажмите кнопку **Attach**.
    ![image3](images/image3.png)
2. В **присоединение баз данных** поле, в разделе **базы данных для присоединения**, нажмите кнопку **добавить** и выберите **файлы SUSDB.mdf** файл (копируется из Папка WID), а затем нажмите кнопку **ОК**.
    ![image4](images/image4.png) ![image5](images/image5.png)

> [!TIP]
> Это также может осуществляться с помощью Transact-Sql.  См. в разделе [документацию по SQL для присоединения базы данных](https://docs.microsoft.com/sql/relational-databases/databases/attach-a-database) его инструкции.
>
> Пример (с использованием пути из предыдущего примера):
> ```sql
>    USE master;
>    GO
>    CREATE DATABASE SUSDB
>    ON
>        (FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data\SUSDB.mdf'),
>        (FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log\SUSDB_Log.ldf')
>        FOR ATTACH;
>    GO
>```

### <a name="verify-sql-server-and-database-logins-and-permissions"></a>Проверить SQL Server и имена входа базы данных и разрешения

#### <a name="sql-server-login-permissions"></a>Разрешения имени входа SQL Server

После присоединения базу данных SUSDB, убедитесь, что **NT AUTHORITY\NETWORK SERVICE** есть разрешения на вход в экземпляр SQL Server следующим образом:

1. Перейти в SQL Server Management Studio
2. Открытие экземпляра
3. Нажмите кнопку **безопасности**
4. Нажмите кнопку **имена входа**

**NT AUTHORITY\NETWORK SERVICE** должна быть указана учетная запись. Если это не так, необходимо добавить его, добавив новое имя входа.

> [!IMPORTANT]
> Если экземпляр SQL установлен на компьютере, отличном от WSUS, учетная запись компьютера сервера WSUS должно быть указано в формате **[полное доменное имя]\\[WSUSComputerName] $** .  Если нет, указанные ниже действия позволяют добавить его, заменив **NT AUTHORITY\NETWORK SERVICE** с учетной записью компьютера сервера WSUS ( **[полное доменное имя]\\[WSUSComputerName] $** ) это было бы ***в дополнение к*** прав **NT AUTHORITY\NETWORK SERVICE**

##### <a name="adding-nt-authoritynetwork-service-and-granting-it-rights"></a>Добавление NT AUTHORITY\NETWORK SERVICE и предоставления ему права

1. Щелкните правой кнопкой мыши **имена входа** и нажмите кнопку **новое имя входа...**
    ![image6](images/image6.png)
2. На **Общие** заполните **имя входа** (**NT AUTHORITY\NETWORK SERVICE**) и задайте **база данных по умолчанию** для SUSDB.
    ![image7](images/image7.png)
3. На **ролей сервера** странице **открытый** и **sysadmin** выбраны.
    ![image8](images/image8.png)
4. На **сопоставления** страницы:
    - В разделе **пользователи, сопоставленные с этим именем входа**: выберите **SUSDB**
    - В разделе **членство в роли для базы данных: SUSDB**, убедитесь, проверяются следующие:
        - **Public**
        - **веб-службы** ![image9](images/image9.png)
5. Нажмите кнопку **ОК**

Теперь вы увидите **NT AUTHORITY\NETWORK SERVICE** под именами входа.
![image10](images/image10.png)

#### <a name="database-permissions"></a>Разрешения базы данных

1. Щелкните правой кнопкой мыши базу данных SUSDB
2. Выберите **свойства**
3. Нажмите кнопку **разрешения**

**NT AUTHORITY\NETWORK SERVICE** должна быть указана учетная запись.

1. Если это не так, добавьте учетную запись.
2. В текстовое поле имя входа введите машины WSUS в следующем формате:
    > [**Полное доменное имя]\\[WSUSComputerName] $**
3. Убедитесь, что **база данных по умолчанию** присваивается **SUSDB**.

    > [!TIP]
    > В следующем примере — это полное доменное имя **Contosto.com** и имя компьютера WSUS — **WsusMachine**:
    >
    > ![Image11](images/image11.png)

4. На **сопоставления** выберите **SUSDB** базы данных в группе **«Пользователи, сопоставленные с этим именем входа»**
5. Проверьте **веб-службы** под **«членство в роли для базы данных: SUSDB"** :  ![image12](images/image12.png)
6. Нажмите кнопку **ОК** сохранить параметры.
    > [!NOTE]
    > Может потребоваться перезапустить службу SQL, чтобы изменения вступили в силу.

### <a name="edit-the-registry-to-point-wsus-to-the-sql-server-instance"></a>Внести изменения в реестр точки WSUS к экземпляру SQL Server

> [!IMPORTANT]
> Внимательно выполните действия, описанные в этом разделе. Неправильное изменение реестра может привести к серьезным проблемам. Перед внесением изменений [создать резервную копию реестра для последующего восстановления](https://support.microsoft.com/en-us/help/322756) в случае возникновения проблем.

1. В меню **Пуск** выберите пункт **Выполнить**, введите **regedit** и нажмите кнопку **ОК**.
2. Найдите следующий раздел: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\UpdateServices\Server\Setup\SqlServerName**
3. В **значение** текстовое поле, тип **[ServerName]\\[имя_экземпляра]** , а затем нажмите кнопку **ОК**. Если имя экземпляра является экземпляром по умолчанию, введите **[ServerName]** .
4. Найдите следующий раздел: **Services\Server\Setup\Installed роли HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Update Services\UpdateServices-WidDatabase** ![image13](images/image13.png)
5. Переименование ключа для **UpdateServices-Database** ![image41](images/image14.png)

    > [!NOTE]
    > Если не обновить этот ключ затем **WsusUtil** попытается службы внутренней базы данных Windows, а не экземпляра SQL, к которому вы перенесли.

### <a name="start-the-iis-and-wsus-services-on-the-wsus-server"></a>Запустите службы IIS и службы WSUS на сервере WSUS

С помощью PowerShell (с повышенными правами) выполните следующую команду:

```powershell
    Start-Service IISADMIN
    Start-Service WsusService
```

> [!NOTE]
> Если вы используете консоль WSUS, закройте и перезапустите его.

## <a name="uninstalling-the-wid-role-not-recommended"></a>При удалении роли внутренней базы данных Windows (не рекомендуется)

> [!WARNING]
> При удалении роли WID также удаляется папки базы данных ( **%SystemDrive%\Program Files\Update Services\Database**), содержащий скрипты, необходимые для выполнения задач после установки WSUSUtil.exe. Если вы решили удалить роль WID, убедитесь, что резервное копирование **%SystemDrive%\Program Files\Update Services\Database** папку заранее.

С помощью PowerShell.

```powershell
Uninstall-WindowsFeature -Name 'Windows-Internal-Database'
```

После удаления роли WID, убедитесь, что следующий раздел реестра: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Update Services\Server\Setup\Installed роли Services\UpdateServices базами данных**