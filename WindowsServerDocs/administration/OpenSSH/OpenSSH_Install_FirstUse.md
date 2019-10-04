---
ms.date: 09/27/2019
ms.topic: conceptual
keywords: OpenSSH, SSH, SSHD, установка, установка
contributor: maertendMSFT
author: maertendMSFT
title: Установка OpenSSH для Windows
ms.openlocfilehash: 3c742e20432d20ea3c402af66f19a803ea1f3a56
ms.sourcegitcommit: 73898afec450fb3c2f429ca373f6b48a74b19390
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2019
ms.locfileid: "71934931"
---
# <a name="installation-of-openssh-for-windows-server-2019-and-windows-10"></a>Установка OpenSSH для Windows Server 2019 и Windows 10 #

Клиент OpenSSH и сервер OpenSSH являются отдельными устанавливаемыми компонентами в Windows Server 2019 и Windows 10 1809.
Пользователи с этими версиями Windows должны использовать приведенные ниже инструкции для установки и настройки OpenSSH. 

> [!NOTE] 
> Пользователи, получившие OpenSSH из репозитория GitHub PowerShell (https://github.com/PowerShell/OpenSSH-Portable) должны использовать инструкции из него и __не должны__ использовать эти инструкции). 


## <a name="installing-openssh-from-the-settings-ui-on-windows-server-2019-or-windows-10-1809"></a>Установка OpenSSH из пользовательского интерфейса параметров в Windows Server 2019 или Windows 10 1809

Клиент OpenSSH и сервер являются устанавливаемыми компонентами Windows 10 1809. 

Чтобы установить OpenSSH, запустите параметры и перейдите к разделу приложения > приложения и компоненты > Управление дополнительными функциями. 

Просмотрите этот список, чтобы узнать, установлен ли клиент OpenSSH. В противном случае в верхней части страницы выберите "добавить компонент", а затем: 

* Чтобы установить клиент OpenSSH, найдите "клиент OpenSSH" и нажмите кнопку "установить". 
* Чтобы установить сервер OpenSSH, найдите "сервер OpenSSH" и нажмите кнопку "установить". 

После завершения установки вернитесь в раздел приложения > приложения и компоненты > управления дополнительными компонентами, и вы увидите список компонентов OpenSSH.

> [!NOTE]
> Установка сервера OpenSSH создаст и включит правило брандмауэра с именем OpenSSH-Server-in-TCP. Это разрешает входящий трафик SSH через порт 22. 

## <a name="installing-openssh-with-powershell"></a>Установка OpenSSH с помощью PowerShell 

Чтобы установить OpenSSH с помощью PowerShell, сначала запустите PowerShell от имени администратора.
Чтобы убедиться, что функции OpenSSH доступны для установки, выполните следующие действия.

```powershell
Get-WindowsCapability -Online | ? Name -like 'OpenSSH*'

# This should return the following output:

Name  : OpenSSH.Client~~~~0.0.1.0
State : NotPresent
Name  : OpenSSH.Server~~~~0.0.1.0
State : NotPresent
```

Затем установите серверные и/или клиентские компоненты.

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

## <a name="uninstalling-openssh"></a>Удаление OpenSSH

Чтобы удалить OpenSSH с помощью параметров Windows, запустите параметры, а затем последовательно выберите приложения > приложения и компоненты > Управление дополнительными компонентами. В списке установленных компонентов выберите компонент Клиент OpenSSH или сервер OpenSSH, а затем щелкните Удалить.

Чтобы удалить OpenSSH с помощью PowerShell, выполните одну из следующих команд:

```powershell
# Uninstall the OpenSSH Client
Remove-WindowsCapability -Online -Name OpenSSH.Client~~~~0.0.1.0

# Uninstall the OpenSSH Server
Remove-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0
```

После удаления OpenSSH может потребоваться перезагрузка Windows, если служба используется в то время, когда она была удалена.


## <a name="initial-configuration-of-ssh-server"></a>Начальная настройка SSH-сервера

Чтобы настроить сервер OpenSSH для первоначального использования в Windows, запустите PowerShell от имени администратора, а затем выполните следующие команды, чтобы запустить службу SSHD:

```powershell
Start-Service sshd
# OPTIONAL but recommended:
Set-Service -Name sshd -StartupType 'Automatic'
# Confirm the Firewall rule is configured. It should be created automatically by setup. 
Get-NetFirewallRule -Name *ssh*
# There should be a firewall rule named "OpenSSH-Server-In-TCP", which should be enabled
# If the firewall does not exist, create one
New-NetFirewallRule -Name sshd -DisplayName 'OpenSSH Server (sshd)' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22
```

## <a name="initial-use-of-ssh"></a>Начальное использование SSH

После установки сервера OpenSSH в Windows можно быстро протестировать его с помощью PowerShell на любом устройстве Windows с установленным клиентом SSH. В PowerShell введите следующую команду: 

```powershell
Ssh username@servername
```

Первое подключение к любому серверу приведет к появлению примерно следующего сообщения:

```
The authenticity of host 'servername (10.00.00.001)' can't be established.
ECDSA key fingerprint is SHA256:(<a large string>).
Are you sure you want to continue connecting (yes/no)?
```

Ответ должен иметь значение "Да" или "нет". Ответ да приведет к добавлению этого сервера в список известных узлов SSH в локальной системе.

На этом этапе вам будет предложено ввести пароль. В целях безопасности пароль не будет отображаться при вводе. 

После подключения вы увидите командную оболочку, аналогичную следующей:

```
domain\username@SERVERNAME C:\Users\username>
```

Оболочкой по умолчанию, используемой сервером Windows OpenSSH, является Командная оболочка Windows. 

