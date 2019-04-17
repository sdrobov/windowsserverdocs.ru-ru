---
ms.assetid: 4deff06a-d0ef-4e5a-9701-5911ba667201
title: "Средство ускоренного AD FS восстановления"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 02/20/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: cd1cc8dab07288ba73c507bc551f089bb79502bc
ms.sourcegitcommit: 36d7b1dfd7da8e9f303d007a628e76149de000f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2018
---
# <a name="ad-fs-rapid-restore-tool"></a>Средство ускоренного AD FS восстановления

>Область применения: Windows Server 2016, Windows Server 2012 R2

## <a name="overview"></a>Обзор
Сегодня AD FS стало высокой доступности благодаря настройке фермы AD FS. В некоторых организациях хотели бы способ с одним сервером развертывания AD FS, устраняя необходимость для нескольких серверов AD FS и балансировки инфраструктуры, но по-прежнему некоторые сетевой нагрузки гарантию того, что служба может быть быстро восстановлена Если возникла проблема.
Новые средства быстрого восстановления AD FS позволяет восстановить данные AD FS без необходимости полного резервного копирования и восстановления состояния системы или операционной системы. Новое средство можно использовать для экспорта конфигурации Служб федерации Active Directory, Azure или в локальную папку.  Затем можно применить экспортируемых данных для новой установки AD FS, повторное создание или дублирование среды AD FS. 

## <a name="scenarios"></a>Сценарии
Средство Быстрое восстановление AD FS можно использовать в следующих случаях:

1. Быстрое восстановление функциональности AD FS после проблема
    - Используйте средство для создания холодной ожидания установки Служб федерации Active Directory, который можно быстро развернуть вместо online сервера AD FS
2. Развертывание идентичные тестовой и рабочей среды
    - Используйте средство быстро создать точную копию производственных Служб федерации Active Directory в тестовой среде или в рабочей среде быстро развернуть проверенные тестовой конфигурации

## <a name="what-is-backed-up"></a>Объекты для резервного копирования
Средство выполняет резервное копирование следующих конфигурации AD FS
    
- AD FS конфигурации базы данных (SQL Server или внутренней базы данных Windows)
- Файл конфигурации (расположен в папке AD FS)
- Автоматически создается маркер подписи и расшифровки сертификаты и закрытые ключи (из контейнера Active Directory DKM)
- SSL-сертификат и все внешние сертификаты для сертификатов (сертификат для подписи маркера маркеров и для взаимодействия служб) и соответствующие закрытые ключи (Примечание: закрытые ключи должны быть экспортируемым и выполнения сценария пользователь должен иметь доступ к ним)
- Список настраиваемых поставщиков проверки подлинности, хранилищах атрибутов и поставщика утверждений локального доверия, которые установлены.

## <a name="how-to-use-the-tool"></a>Как использовать средство
Во-первых, [загрузить](https://go.microsoft.com/fwlink/?LinkId=825646) и установки MSI для сервера AD FS.  

>[!NOTE]
>AD FS быстрое средство восстановления не совместим со стандартом FIPS.

Выполните следующую команду из командной строки PowerShell:

```powershell
import-module 'C:\Program Files (x86)\ADFS Rapid Recreation Tool\ADFSRapidRecreationTool.dll'
```

>[!NOTE] 
>При использовании встроенной базы данных Windows (WID), это средство необходимо запустить на основном сервере Служб федерации Active Directory.  Можно использовать `Get-SyncProperties` командлет PowerShell для определения того, является ли сервер используется является основным сервером.

### <a name="system-requirements"></a>Требования к системе

- Это средство вместе для служб AD FS в Windows Server 2012 R2 и более поздних версий. 
- Требуется .NET framework — по крайней мере 4.0. 
- Восстановление должна выполняться на сервере AD FS ту же версию резервной копии и, использующей одной и той же учетной записью Active Directory в качестве учетной записи службы AD FS.

## <a name="create-a-backup"></a>Создание резервной копии
Создание резервной копии, используйте командлет ADFS резервного копирования. Этот командлет создает резервную копию конфигурации AD FS, база данных, SSL-сертификаты, и т. д. 

Пользователь должен быть по крайней мере локального администратора для выполнения этого командлета. Для создания резервной копии контейнер Active Directory DKM (требуется в конфигурации по умолчанию AD FS), пользователь должен быть администратором домена также либо необходимости передачи учетных данных учетной записи службы AD FS.

Резервное копирование будет называться в соответствии с шаблоном «adfsBackup_ID_Date время». Она будет содержать номер версии, Дата и время, которое было выполнено резервное копирование.
Командлет принимает следующие параметры:
    
Наборы параметров

![Средство ускоренного AD FS восстановления](media/AD-FS-Rapid-Restore-Tool/parameter1.png)

### <a name="detailed-description"></a>Подробное описание

- **BackupDKM** -архивирует контейнер Active Directory DKM, содержащую ключи AD FS в конфигурации по умолчанию (автоматически созданный маркер подписи и расшифровки сертификатов). Средство AD «ldifde» используется для экспорта контейнера Рекламы, а также все его ветви.

- -**StorageType &lt;строка&gt; ** -типа хранилища, пользователю необходимо использовать. «Файловая система» указывает, что пользователь хочет сохранить его в папке локально или в сети, «Azure» указывает пользователь хочет сохранить его в контейнере хранилища Azure, когда пользователь выполняет резервное копирование, они выберите расположение резервной копии файловой системы или в облаке. Для Azure для использования учетных данных Azure хранилища должны передаваться в командлет. Хранилище учетных данных содержит имя учетной записи и ключа. Кроме того имя контейнера должны быть переданы в. Если контейнер не существует, он будет создан во время архивации. Для файловой системы для использования нужно задать путь к хранилищу. В этом каталоге нового каталога создается для каждой операции резервного копирования. Каждая папка, созданная будет содержать файлы резервных копий. 

- **EncryptionPassword &lt;строка&gt; ** -пароль, который будет использоваться для шифрования архивированного файлы перед ее сохранением

- **AzureConnectionCredentials &lt;pscredential&gt; ** -имя учетной записи и ключа для учетной записи службы хранилища Azure

- **AzureStorageContainer &lt;строка&gt; ** -контейнер хранения, где будут храниться резервного копирования в Azure

- **StoragePath &lt;строка&gt; ** -расположение архивы будут храниться в

- **ServiceAccountCredential &lt;pscredential&gt; ** -указывает учетной записи службы, используемый для службы AD FS, в данный момент выполняется. Этот параметр требуется только в том случае, если пользователь предпочитает для резервного копирования DKM и не администратора домена.

- **BackupComment &lt;string []&gt; ** -строку информационное сообщение о системе архивации данных, который будет отображаться во время восстановления, аналогично концепцию именования контрольной точки Hyper-V. По умолчанию является пустой строкой

 
## <a name="backup-examples"></a>Примеры резервного копирования
Ниже приведены примеры резервного копирования для средства AD FS быстрое восстановление.

### <a name="backup-the-ad-fs-configuration-with-the-dkm-to-the-file-system-while-running-as-the-domain-admin"></a>Создайте резервную копию конфигурации AD FS, с помощью DKM, в файловой системе, в ходе выполнения от имени администратора домена

```powershell
Backup-ADFS -StorageType "FileSystem" -StoragePath "C:\Users\administrator\testExport\" -EncryptionPassword "password" -BackupComment "Clean Install of ADFS (FS)" -BackupDKM
```
 
### <a name="backup-the-ad-fs-configuration-with-the-dkm-to-the-file-system-with-the-service-account-credential-running-as-local-admin"></a>Конфигурация резервного копирования AD FS с DKM, в файловой системе с помощью учетных данных учетной записи службы, работающему под учетной записью локального администратора

```powershell
Backup-ADFS -StorageType "FileSystem" -StoragePath "C:\Users\administrator\testExport\" -EncryptionPassword "password" -BackupComment "Clean Install of ADFS (FS)" -BackupDKM -ServiceAccountCredential $cred
```

### <a name="backup-the-ad-fs-configuration-without-the-dkm-to-the-azure-storage-container"></a>Создайте резервную копию конфигурации AD FS без DKM контейнер хранилища Azure.

```powershell
Backup-ADFS -StorageType "Azure" -AzureConnectionCredentials $cred -AzureStorageContainer "adfsbackups"  -EncryptionPassword "password" -BackupComment "Clean Install of ADFS"
```

### <a name="backup-the-ad-fs-configuration-without-the-dkm-to-the-file-system"></a>Создайте резервную копию конфигурации AD FS без DKM в файловой системе

```powershell   
Backup-ADFS -StorageType "FileSystem" -StoragePath "C:\Users\administrator\testExport\" -EncryptionPassword "password" -BackupComment "Clean Install of ADFS (FS)"
```

## <a name="restore-from-backup"></a>Восстановление из резервной копии
Для применения конфигурации, созданный с помощью ADFS резервного копирования для новой установки AD FS, используйте командлет Restore-служб федерации Active Directory.

Этот командлет создает новой ферме AD FS с помощью командлета `Install-AdfsFarm` и восстанавливает конфигурацию AD FS, база данных, сертификаты, и т. д. Если роль Служб федерации Active Directory не было установлено на сервере, командлет будет установить.  Командлет проверяет расположения для существующие архивы восстановления и предлагает пользователю выбрать соответствующий резервного копирования, на основе даты и времени создания и любые комментарии резервного копирования, пользователь может подключенный к резервной копии. При наличии нескольких конфигураций Служб федерации Active Directory с именами служб федерации другой, пользователю предлагается сначала выбрать соответствующую конфигурацию AD FS.
Пользователь должен быть локальной и доменной администратора для выполнения этого командлета.


>[!NOTE] 
>Перед использованием средства быстрого восстановления AD FS, убедитесь, что сервер присоединен к домену до восстановления резервной копии. 

Командлет принимает следующие параметры: 

![Средство ускоренного AD FS восстановления](media/AD-FS-Rapid-Restore-Tool/parameter2.png)

### <a name="detailed-description"></a>Подробное описание

- **StorageType &lt;строка&gt; ** -типа хранилища, пользователю необходимо использовать.
 «Файловая система» означает, что пользователь хочет сохранить его в папку локально или в сети «Azure» означает, что пользователь хочет сохранить его в контейнере хранилища Azure

- **DecryptionPassword &lt;строка&gt; ** -пароль, который использовался для шифрования архивных файлов 

- **AzureConnectionCredentials &lt;pscredential&gt; ** -имя учетной записи и ключа для учетной записи службы хранилища Azure

- **AzureStorageContainer &lt;строка&gt; ** -контейнер хранения, где будут храниться резервного копирования в Azure

- **StoragePath &lt;строка&gt; ** -расположение архивы будут храниться в

- **ADFSName &lt; строка &gt; ** -имя федерации, резервного копирования и планируется восстановить. Если данный параметр не указан, а имя службы федерации только один то, будет использоваться. Если существует более одной службы федерации резервное копирование в расположения, а затем пользователю будет предложено выбрать один из резервной копии службы федерации.

- **ServiceAccountCredential &lt; pscredential &gt; ** -указывает учетной записи службы, которая будет использоваться для новой службы AD FS восстанавливаемый 

- **GroupServiceAccountIdentifier &lt;строка&gt; ** -групповой управляемой учетной записи, пользователю необходимо использовать для новой службы AD FS восстанавливается. По умолчанию Если ни один предоставляется резервной копии имя учетной записи используется, если он был групповой управляемой учетной записи, else пользователю предлагается установить в учетной записи службы

- **DBConnectionString &lt;строка&gt; ** — Если пользователь предпочитает на использование другой базы данных для восстановления, то их следует передать строки подключения SQL или тип внутренней базы данных Windows для WID.

- **Принудительное &lt;bool&gt; ** -пропустить запросы, которые средство, возможно, после выбора резервного копирования

- **RestoreDKM &lt;bool&gt; ** - восстановите контейнер DKM с AD, необходимо установить, если планируется новую Рекламу и DKM выполнялось резервное копирование изначально.

## <a name="restore-examples"></a>Восстановление примеры

### <a name="restore-the-ad-fs-configuration-without-the-dkm-from-the-azure-storage-container"></a>Восстановление конфигурации AD FS без DKM из контейнера хранилища Azure

```powershell
Restore-ADFS -StorageType "Azure" -AzureConnectionCredential $cred -DecryptionPassword "password" -AzureStorageContainer "adfsbackups"
```

### <a name="restore-the-ad-fs-configuration-without-the-dkm-from-the-file-system"></a>Восстановление конфигурации AD FS без DKM из файловой системы
 
```powershell
Restore-ADFS -StorageType "FileSystem" -StoragePath "C:\uSERS\administrator\testExport\" -DecryptionPassword "password"
```

### <a name="restore-the-ad-fs-configuration-with-the-dkm-to-the-file-system"></a>Восстановление конфигурации AD FS с помощью DKM в файловой системе 
 
```powershell
Restore-ADFS -StorageType "FileSystem" -StoragePath "C:\uSERS\administrator\testExport\" -DecryptionPassword "password" -RestoreDKM
```

### <a name="restore-the-ad-fs-configuration-to-wid"></a>Восстановление конфигурации AD FS для внутренней базы данных Windows

```powershell
Restore-ADFS -StorageType "FileSystem" -StoragePath "C:\uSERS\administrator\testExport\" -DecryptionPassword "password" -DBConnectionString "WID"
``` 

### <a name="restore-the-ad-fs-configuration-to-sql"></a>Восстановление конфигурации AD FS к SQL Server

```powershell
Restore-ADFS -StorageType "FileSystem" -StoragePath "C:\uSERS\administrator\testExport\" -DecryptionPassword "password" -DBConnectionString "Data Source=TESTMACHINE\SQLEXPRESS; Integrated Security=True"
```

### <a name="restores-the-ad-fs-configuration-with-the-specified-gmsa"></a>Восстановление конфигурации AD FS с указанным групповой управляемой учетной записи

```powershell
Restore-ADFS -StorageType "FileSystem" -StoragePath "C:\uSERS\administrator\testExport\" -DecryptionPassword "password" -GroupServiceAccountIdentifier "mangupd1\adfsgmsa$"
```
### <a name="restore-the-ad-fs-configuration-with-the-specified-service-account-creds"></a>Восстановление конфигурации AD FS с учетные данные учетной записи службы

```powershell
Restore-ADFS -StorageType "FileSystem" -StoragePath "C:\uSERS\administrator\testExport\" -DecryptionPassword "password" -ServiceAccountCredential $cred
```

## <a name="encryption-information"></a>Сведения о шифровании
Все данные резервного копирования, шифруются перед помещает его в облако или сохранить его в файловой системе.  

Каждый документ, созданный в процессе резервного копирования, зашифрован с помощью AES-256. Пароль передается в средство используется как парольную фразу, чтобы создать новый пароль, с помощью класса Rfc2898DeriveBytes. 

RngCryptoServiceProvider используется для создания salt, используемые AES и Rfc2898DeriveBytes класса. 

## <a name="log-files"></a>Файлы журналов
Каждый раз при выполнении резервного копирования или восстановления создается файл журнала. Их можно найти в следующем расположении:

- **%LocalAppData%\ADFSRapidRecreationTool**

>[!NOTE]
> При выполнении восстановления, который может создать файл PostRestore_Instructions обзором поставщиков дополнительной проверки подлинности хранилищ атрибутов и отношения доверия с поставщиком утверждений локального устанавливаемые вручную перед запуском службы AD FS.
