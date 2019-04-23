---
ms.date: 01/07/2019
ms.topic: conceptual
keywords: OpenSSH, SSH, SSHD, установка, Настройка
contributor: maertendMSFT
author: maertendMSFT
title: Установка OpenSSH для Windows
ms.openlocfilehash: f617b01ee7dabd4897f99e374420f673e209e145
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59859565"
---
# <a name="installation-of-openssh-for-windows-server-2019-and-windows-10"></a>Установка OpenSSH для Windows Server 2019 г. и Windows 10 #

Клиент OpenSSH и OpenSSH Server находятся отдельно устанавливаемых компонентов в Windows Server 2019 и Windows 10 1809.
Пользователи с помощью этих версий Windows следует использовать, следуйте инструкциям по установке и настройке OpenSSH. 

> [!NOTE] 
> Пользователей, которые приобрели OpenSSH из репозитория PowerShell Github (https://github.com/PowerShell/OpenSSH-Portable) следует использовать инструкции из этого и __не должны__ используйте эти инструкции. 


## <a name="installing-openssh-from-the-settings-ui-on-windows-server-2019-or-windows-10-1809"></a>Установка OpenSSH в параметрах пользовательского интерфейса в Windows Server 2019 г. или Windows 10 1809

Клиент OpenSSH и сервер находятся устанавливаемые функции Windows 10 1809. 

Чтобы установить OpenSSH, запустите параметры, затем перейдите в раздел приложения > программы и компоненты > Управление дополнительных функций. 

Проверьте этот список, чтобы увидеть, установлен ли клиент OpenSSH. Если нет, затем в верхней части страницы выберите «Добавить компонент», а затем: 

* Чтобы установить клиент OpenSSH, найдите «Клиент OpenSSH», а затем нажмите кнопку «Установить». 
* Чтобы установить сервер OpenSSH, найдите «OpenSSH Server», а затем нажмите кнопку «Установить». 

После завершения установки вернитесь к приложений > программы и компоненты > Управление дополнительные функции и увидеть в списке компонентов OpenSSH.

> [!NOTE]
> Установка сервера OpenSSH Создание и включение правила брандмауэра с именем «OpenSSH-Server-в-TCP». Это разрешает входящий трафик SSH через порт 22. 

## <a name="installing-openssh-with-powershell"></a>Установка OpenSSH с помощью PowerShell 

Чтобы установить OpenSSH, с помощью PowerShell, сначала запустите PowerShell от имени администратора.
Чтобы убедиться в том, что функции OpenSSH, доступны для установки:

```powershell
Get-WindowsCapability -Online | ? Name -like 'OpenSSH*'

# This should return the following output:

Name  : OpenSSH.Client~~~~0.0.1.0
State : NotPresent
Name  : OpenSSH.Server~~~~0.0.1.0
State : NotPresent
```

Затем установите компоненты сервера и клиента:

```powershell
# Install the OpenSSH Client
Add-WindowsCapability -Online -Name OpenSSH.Client~~~~0.0.1.0

# Install the OpenSSH Server
Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0

# Both of these should return the following output:

Path          :
Online        : True
RestartNeeded : False
```

## <a name="uninstalling-openssh"></a>При удалении OpenSSH

Чтобы удалить OpenSSH, с помощью параметров Windows, параметры запуска, то перейдите в раздел приложения > программы и компоненты > Управление дополнительных функций. В списке установленных компонентов выберите компонент Клиент OpenSSH или OpenSSH Server, а затем выберите Удалить.

Чтобы удалить OpenSSH, с помощью PowerShell, используйте один из следующих команд:

```powershell
# Uninstall the OpenSSH Client
Remove-WindowsCapability -Online -Name OpenSSH.Client~~~~0.0.1.0

# Uninstall the OpenSSH Server
Remove-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0
```

После удаления OpenSSH, если служба используется во время она была удалена, может потребоваться перезагрузка Windows.


## <a name="initial-configuration-of-ssh-server"></a>Начальной настройки сервера SSH

Для настройки сервера OpenSSH для первого использования на Windows, запустите PowerShell с правами администратора, а затем выполните следующие команды, чтобы запустить службу SSHD:

```powershell
Start-Service sshd
# OPTIONAL but recommended:
Set-Service -Name sshd -StartupType 'Automatic'
# Confirm the Firewall rule is configured. It should be created automatically by setup. 
Get-NetFirewallRule -Name *ssh*
# There should be a firewall rule named "OpenSSH-Server-In-TCP", which should be enabled 
```

## <a name="initial-use-of-ssh"></a>Использование начального SSH

После установки OpenSSH Server на Windows, вы можете быстро проверить с помощью Windows PowerShell с любого устройства Windows с помощью SSH установлен клиент. В PowerShell введите следующую команду: 

```powershell
Ssh username@servername
```

Первое подключение к любому серверу приведет к сообщение, аналогичное приведенному ниже:

```
The authenticity of host 'servername (10.00.00.001)' can't be established.
ECDSA key fingerprint is SHA256:(<a large string>).
Are you sure you want to continue connecting (yes/no)?
```

Ответ должен быть либо «yes» или «no». Положительный ответ в локальной системе добавить сервер в список известных ssh узлов.

Вам предложат ввести пароль на этом этапе. По соображениям безопасности ваш пароль не будет отображаться, при вводе. 

После подключения вы увидите командной оболочки следующего вида:

```
domain\username@SERVERNAME C:\Users\username>
```

Оболочка по умолчанию, используемые сервером Windows OpenSSH — это командная оболочка Windows. 

