---
ms.date: 09/27/2018
ms.topic: conceptual
keywords: OpenSSH, SSH, SSHD, установка, Настройка
contributor: maertendMSFT
ms.product: w10
author: maertendMSFT
title: Конфигурация сервера OpenSSH для Windows
ms.openlocfilehash: 7eff3d3e1af67c9daf7a68c67c3609c0ee89fc93
ms.sourcegitcommit: afb0602767de64a76aaf9ce6a60d2f0e78efb78b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/20/2019
ms.locfileid: "67280035"
---
# <a name="openssh-server-configuration-for-windows-10-1809-and-server-2019"></a>Конфигурация сервера OpenSSH для Windows 10 1809 и Server 2019#

В этом разделе конфигурации Windows для сервера OpenSSH (sshd). 

OpenSSH хранит подробную документацию для параметров конфигурации сети на [OpenSSH.com](https://www.openssh.com/manual.html), который является не будут скопированы в этот набор документации. 

## <a name="configuring-the-default-shell-for-openssh-in-windows"></a>Настройка оболочки по умолчанию для OpenSSH в Windows

По умолчанию командная оболочка предоставляет интерфейс, который пользователь видит при подключении к серверу, с помощью SSH. Начальное значение по умолчанию Windows — Windows командной оболочки (cmd.exe). Также включает Windows PowerShell и Bash и командных оболочках третьих лиц, также доступны для Windows и могут использоваться в качестве оболочки по умолчанию для сервера.

Чтобы задать командную оболочку по умолчанию, сначала убедитесь в папке установки OpenSSH в системном пути. Для Windows в папку установки по умолчанию является SystemDrive:WindowsDirectory\System32\openssh. Следующие команды показывает текущее значение параметра path и добавьте папку установки по умолчанию OpenSSH к нему. 

Командная оболочка | Команду, чтобы использовать
------------- | -------------- 
Command | path
PowerShell | $env:path

Настройка по умолчанию ssh shell выполняется в реестре Windows, добавив полный путь к исполняемому файлу Computer\HKEY_LOCAL_MACHINE\SOFTWARE\OpenSSH в строковом параметре DefaultShell оболочки. 

Например следующую команду Powershell задает быть PowerShell.exe оболочку по умолчанию:

```powershell
New-ItemProperty -Path "HKLM:\SOFTWARE\OpenSSH" -Name DefaultShell -Value "C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe" -PropertyType String -Force
```

## <a name="windows-configurations-in-sshdconfig"></a>Конфигураций Windows в sshd_config 

В Windows sshd считывает данные конфигурации из %programdata%\ssh\sshd_config по умолчанию или другого файла конфигурации можно составить, запустив sshd.exe с параметром -f.
Если файл отсутствует, sshd он создается с конфигурацией по умолчанию при запуске службы.

Элементы, перечисленные ниже предоставляют конфигурации, относящиеся к Windows ставшего возможным благодаря записей в sshd_config. Существуют другие параметры конфигурации в, не перечисленных здесь, как они подробно описаны в документации [документации Win32 OpenSSH](https://github.com/powershell/win32-openssh/wiki). 


### <a name="allowgroups-allowusers-denygroups-denyusers"></a>AllowGroups DenyUsers AllowUsers DenyGroups, 

Управление, каким пользователям и группам можно соединиться с сервером выполняется с помощью директив AllowGroups, AllowUsers, DenyGroups и DenyUsers. Разрешить или запретить директивы, обрабатываются в следующем порядке: DenyUsers, AllowUsers, DenyGroups и наконец AllowGroups. Все имена учетных записей необходимо указать в нижнем регистре. См. в разделе ШАБЛОНОВ в ssh_config Дополнительные сведения о шаблонах для подстановочных знаков.

При настройке пользователя или группы на основе правил домена пользователя или группы, используйте следующий формат: ``` user?domain* ```.
Windows позволяет несколько форматов для указания домена субъекты, но многие противоречит стандартные шаблоны Linux. По этой причине * добавляется для охвата полные доменные имена. Кроме того, этот подход использует «?», а не @, чтобы избежать конфликтов с username@host формат. 

Рабочие группы пользователей или групп и учетных записей, подключенной к Интернету всегда разрешаются до своего имени локальной учетной записи (не доменной частью, аналогичную стандартные имена в Unix). Пользователи и группы домена относятся исключительно к [NameSamCompatible](https://docs.microsoft.com/windows/desktop/api/secext/ne-secext-extended_name_format) формат — domain_short_name\user_name. Всех пользователей или групп на основе конфигурации, что правила нужно соблюдать этот формат.

Примеры для пользователей и групп домена 

```
DenyUsers contoso\admin@192.168.2.23 : blocks contoso\admin from 192.168.2.23
DenyUsers contoso\* : blocks all users from contoso domain
AllowGroups contoso\sshusers : only allow users from contoso\sshusers group
```

Примеры для локальных пользователей и групп 

```
AllowUsers localuser@192.168.2.23
AllowGroups sshusers
```

### <a name="authenticationmethods"></a>AuthenticationMethods 

Для Windows OpenSSH только доступные методы проверки подлинности являются «password» и «publickey».

### <a name="authorizedkeysfile"></a>AuthorizedKeysFile 

По умолчанию используется «.ssh/authorized_keys .ssh/authorized_keys2». Если путь не является абсолютным, он берется относительно домашнем каталоге пользователя (или путь к образу профиля). Пример: c:\users\user.

### <a name="chrootdirectory-support-added-in-v7700"></a>ChrootDirectory (поддержка добавлена в v7.7.0.0)

Эта директива поддерживается только с сеансами sftp. Не соблюдает системе удаленного сеанса в cmd.exe. Чтобы настроить сервер sftp только chroot, присвоено ForceCommand внутренней sftp. Также может настроить scp с chroot, путем реализации пользовательской оболочки, которая позволила бы только scp и sftp.

### <a name="hostkey"></a>HostKey

По умолчанию используется % programdata%/ssh/ssh_host_rsa_key programdata%/ssh/ssh_host_ecdsa_key "," %programdata%/ssh/ssh_host_ed25519_key "и" %. Если отсутствуют значения по умолчанию, sshd автоматически создает эти при запуске службы.

### <a name="match"></a>Сопоставление

Обратите внимание, что шаблон правила в этом разделе. Имена пользователей и групп должны быть в нижнем регистре.

### <a name="permitrootlogin"></a>PermitRootLogin

Неприменимо в Windows. Чтобы предотвратить имя входа администратора, используйте администраторов с директивой DenyGroups.

### <a name="syslogfacility"></a>SyslogFacility

Если вам требуется файл на основе ведения журнала, используйте LOCAL0. Журналы создаются в разделе % programdata%\ssh\logs.
Любое другое значение, включая значение по умолчанию AUTH направляет ведение журнала трассировки событий Windows. Дополнительные сведения см. в разделе средства ведения журнала в Windows.

### <a name="not-supported"></a>Не поддерживается. 

Следующие параметры конфигурации не доступны в версии OpenSSH, который поставляется в Windows Server 2019 и Windows 10 1809:

* AcceptEnv
* AllowStreamLocalForwarding
* AuthorizedKeysCommand
* AuthorizedKeysCommandUser
* AuthorizedPrincipalsCommand
* AuthorizedPrincipalsCommandUser
* сжатие;
* ExposeAuthInfo
* GSSAPIAuthentication
* GSSAPICleanupCredentials
* GSSAPIStrictAcceptorCheck
* HostbasedAcceptedKeyTypes
* HostbasedAuthentication
* HostbasedUsesNameFromPacketOnly
* IgnoreRhosts
* IgnoreUserKnownHosts
* KbdInteractiveAuthentication
* KerberosAuthentication
* KerberosGetAFSToken
* KerberosOrLocalPasswd
* KerberosTicketCleanup
* PermitTunnel
* PermitUserEnvironment
* PermitUserRC
* PidFile
* PrintLastLog
* RDomain
* StreamLocalBindMask
* StreamLocalBindUnlink
* StrictModes
* X11DisplayOffset
* X11Forwarding
* X11UseLocalhost
* XAuthLocation

