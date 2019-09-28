---
title: Миграция базы данных WSUS из (внутренняя база данных Windows) WID в SQL
description: Раздел о службе Windows Server Update Service (WSUS). Перенос базы данных WSUS (SUSDB) из экземпляра внутренней базы данных Windows в локальный или удаленный экземпляр SQL Server.
ms.prod: windows-server
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
ms.openlocfilehash: 0977aa1fd9a6848bd7b85bb592b6a82556277e72
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71361576"
---
>Относится к: Windows Server 2012, Windows Server 2012 R2, Windows Server 2016

# <a name="migrating-the-wsus-database-from-wid-to-sql"></a>Миграция базы данных WSUS из WID в SQL

Выполните следующие действия, чтобы перенести базу данных WSUS (SUSDB) из экземпляра внутренней базы данных Windows на локальный или удаленный экземпляр SQL Server.

## <a name="prerequisites"></a>Предварительные требования

- Экземпляр SQL. Это может быть **MSSQLServer** или пользовательский экземпляр по умолчанию.
- SQL Server Management Studio
- WSUS с установленной ролью WID
- IIS (обычно это включается при установке WSUS с помощью диспетчер сервера). Она еще не установлена, она должна быть.

## <a name="migrating-the-wsus-database"></a>Миграция базы данных WSUS

### <a name="stop-the-iis-and-wsus-services-on-the-wsus-server"></a>Останавливает службы IIS и WSUS на сервере WSUS

В PowerShell (с повышенными правами) выполните:

```powershell
    Stop-Service IISADMIN
    Stop-Service WsusService
```

### <a name="detach-susdb-from-the-windows-internal-database"></a>Отсоединение SUSDB от внутренней базы данных Windows

#### <a name="using-sql-management-studio"></a>Использование SQL Management Studio

1. Щелкните правой кнопкой мыши **SUSDB** - @ no__t-2 **tasks** - @ No__t-5 щелкните **Detach**: ![image1 @ no__t-8.
2. Установите флажок **Удалить существующие подключения** и нажмите кнопку **ОК** (необязательно, если существуют активные соединения).
    ![image2 @ no__t-1

#### <a name="using-command-prompt"></a>Использование командной строки

> [!IMPORTANT]
> В этих шагах показано, как отключить базу данных WSUS (SUSDB) из экземпляра внутренней базы данных Windows с помощью программы **sqlcmd** . Дополнительные сведения о программе **sqlcmd** см. в разделе [программа sqlcmd](https://go.microsoft.com/fwlink/?LinkId=81183).
> 1. Открытие командной строки с повышенными привилегиями
> 2. Выполните следующую команду SQL, чтобы отключить базу данных WSUS (SUSDB) из экземпляра внутренней базы данных Windows с помощью программы **sqlcmd** :

```batchfile
        sqlcmd -S \\.\pipe\Microsoft##WID\tsql\query
        use master
        GO
        alter database SUSDB set single_user with rollback immediate
        GO
        sp_detach_db SUSDB
        GO
```

### <a name="copy-the-susdb-files-to-the-sql-server"></a>Скопируйте файлы SUSDB в SQL Server

1. Скопируйте **SUSDB. mdf** и **SUSDB\_log.ldf** из папки данных WID ( **% systemdrive%** \* * Виндовс\вид\дата * *) в папку данных экземпляра SQL.

> [!TIP]
> Например, если папка экземпляра SQL — **C:\Program FILES\MICROSOFT SQL Server\MSSQL12. МССКЛСЕРВЕР\МССКЛ**, а папка данных WID — **к:\виндовс\вид\дата,** скопируйте файлы SUSDB из **К:\виндовс\вид\дата** в папку **C:\Program Files\Microsoft SQL Server\MSSQL12. Мссклсервер\мсскл\дата**

### <a name="attach-susdb-to-the-sql-instance"></a>Присоединение SUSDB к экземпляру SQL

1. В **SQL Server Management Studio**в узле **экземпляр** щелкните правой кнопкой мыши узел **базы данных**и выберите команду **присоединить**.
    ![image3 @ no__t-1
2. В поле **Присоединение баз данных** в разделе **базы данных для присоединения**нажмите кнопку **добавить** , найдите файл **SUSDB. mdf** (скопированный из папки WID) и нажмите кнопку **ОК**.
    ![image4 @ no__t-1 ![image5 @ no__t-3

> [!TIP]
> Это также можно сделать с помощью Transact-SQL.  Дополнительные сведения о [присоединении базы данных](https://docs.microsoft.com/sql/relational-databases/databases/attach-a-database) см. в документации по SQL.
>
> Пример (использование путей из предыдущего примера):
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

### <a name="verify-sql-server-and-database-logins-and-permissions"></a>Проверка SQL Server и имен входа и разрешений базы данных

#### <a name="sql-server-login-permissions"></a>SQL Server разрешения для входа

После подключения SUSDB убедитесь, что **NT Authority\Network Service** имеет разрешения на вход в экземпляр SQL Server, выполнив следующие действия.

1. Переход к SQL Server Management Studio
2. Открытие экземпляра
3. Щелкните **Безопасность** .
4. Щелкните **имена входа**

Должна быть указана учетная запись **NT Authority\Network Service** . Если это не так, необходимо добавить новое имя для входа.

> [!IMPORTANT]
> Если экземпляр SQL находится на другом компьютере из служб WSUS, учетная запись компьютера сервера WSUS должна быть указана в формате **[FQDN] \\ [всускомпутернаме] $** .  В противном случае можно использовать приведенные ниже шаги, чтобы добавить его, заменив **NT Authority\Network Service** учетной записью компьютера сервера WSUS ( **[FQDN] \\ [всускомпутернаме] $** ) это может быть ***дополнение к*** предоставлению прав на **NT Authority \ СЕТЕВая служба**

##### <a name="adding-nt-authoritynetwork-service-and-granting-it-rights"></a>Добавление NT AUTHORITY\NETWORK SERVICE и предоставление ей прав доступа

1. Щелкните правой кнопкой мыши **имена входа** и выберите **создать имя входа...**
    ![image6 @ no__t-1
2. На странице **Общие** введите **имя входа** (**NT Authority\Network Service**) и задайте для **базы данных по умолчанию** значение SUSDB.
    ![image7 @ no__t-1
3. На странице **роли сервера** убедитесь, что выбраны **Общие** и **sysadmin** .
    ![image8 @ no__t-1
4. На странице **Сопоставление пользователей** :
    - В разделе **Пользователи, сопоставленные с этим именем входа**выберите **SUSDB** .
    - В разделе @no__t — членство в роли 0Database для: SUSDB @ no__t-0 убедитесь, что установлены следующие флажки:
        - **закрытый**
        - **webservice** ![image9 @ no__t-2
5. Нажмите кнопку **ОК**

Теперь в разделе имена входа будет отображаться **NT Authority\Network Service** .
![image10 @ no__t-1

#### <a name="database-permissions"></a>Разрешения базы данных

1. Щелкните правой кнопкой мыши SUSDB
2. Выбор **свойств**
3. Щелкните **разрешения** .

Должна быть указана учетная запись **NT Authority\Network Service** .

1. Если это не так, добавьте учетную запись.
2. В текстовом поле Login name (имя входа) введите компьютер WSUS в следующем формате:
    > [**FQDN] \\ [всускомпутернаме] $**
3. Убедитесь, что для **базы данных по умолчанию** задано значение **SUSDB**.

    > [!TIP]
    > В следующем примере полное доменное имя — **Contosto.com** , а имя машины WSUS — **всусмачине**:
    >
    > ![image11](images/image11.png)

4. На странице **Сопоставление пользователей** выберите базу данных **SUSDB** в разделе **"Пользователи, сопоставленные с этим именем входа"** .
5. Установите флажок **WebService** в поле  **"членство в роли базы данных для: SUSDB "** : ![image12 @ no__t-2
6. Нажмите кнопку **ОК** , чтобы сохранить параметры.
    > [!NOTE]
    > Чтобы изменения вступили в силу, может потребоваться перезапустить службу SQL.

### <a name="edit-the-registry-to-point-wsus-to-the-sql-server-instance"></a>Измените реестр, чтобы указать WSUS на экземпляр SQL Server

> [!IMPORTANT]
> Внимательно выполните действия, описанные в этом разделе. Неправильное изменение реестра может привести к серьезным проблемам. Перед внесением изменений [создайте резервную копию реестра для его восстановления](https://support.microsoft.com/en-us/help/322756) в случае возникновения проблем.

1. В меню **Пуск** выберите пункт **Выполнить**, введите **regedit** и нажмите кнопку **ОК**.
2. Откройте следующий раздел: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\UpdateServices\Server\Setup\SqlServerName**
3. В текстовом поле **значение** введите **[SERVERNAME] \\ [имя_экземпляра]** , а затем нажмите кнопку **ОК**. Если имя экземпляра является экземпляром по умолчанию, введите **[SERVERNAME]** .
4. Откройте следующий раздел: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Update Сервицес\сервер\сетуп\инсталлед Role сервицес\упдатесервицес-виддатабасе** ![image13 @ no__t-2
5. Переименуйте ключ в **UpdateServices-Database** ![image41 @ no__t-2.

    > [!NOTE]
    > Если не обновить этот ключ, **WsusUtil** попытается обслуживать WID, а не экземпляр SQL, с которым был осуществлен перенос.

### <a name="start-the-iis-and-wsus-services-on-the-wsus-server"></a>Запуск служб IIS и WSUS на сервере WSUS

В PowerShell (с повышенными правами) выполните:

```powershell
    Start-Service IISADMIN
    Start-Service WsusService
```

> [!NOTE]
> Если вы используете консоль WSUS, закройте и перезапустите ее.

## <a name="uninstalling-the-wid-role-not-recommended"></a>Удаление роли WID (не рекомендуется)

> [!WARNING]
> При удалении роли WID также удаляется папка базы данных ( **%systemdrive%\Program Files\Update сервицес\датабасе**), которая содержит сценарии, необходимые WSUSutil. exe для выполнения задач, выполняемых после установки. Если вы решили удалить роль WID, убедитесь, что создана резервная копия папки **%systemdrive%\Program Files\Update сервицес\датабасе** .

С помощью PowerShell:

```powershell
Uninstall-WindowsFeature -Name 'Windows-Internal-Database'
```

После удаления роли WID убедитесь в наличии следующего раздела реестра: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Update Сервицес\сервер\сетуп\инсталлед роль Сервицес\упдатесервицес-датабасе**