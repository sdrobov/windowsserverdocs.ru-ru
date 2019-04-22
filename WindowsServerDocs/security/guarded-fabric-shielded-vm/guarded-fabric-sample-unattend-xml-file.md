---
title: Создание специализированного файла ответов ОС
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
ms.assetid: 299aa38e-28d2-4cbe-af16-5b8c533eba1f
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 1d9e91ec8f4c998f34e324b5d551a387eba5a310
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59823635"
---
# <a name="create-os-specialization-answer-file"></a>Создание специализированного файла ответов ОС

>Относится к: Windows Server 2019 г., Windows Server (полугодовой канал), Windows Server 2016

В рамках подготовки к развертыванию экранированных виртуальных машин необходимо создать файл ответов специализации операционной системы. В Windows это часто называется «unattend.xml» файла. **New-ShieldingDataAnswerFile** функции Windows PowerShell помогает сделать это. После этого можно использовать файл ответов, при создании экранированных виртуальных машин из шаблона с помощью System Center Virtual Machine Manager (или любой другой контроллер структуры).

Общие рекомендации для файлов автоматической установки для экранированных виртуальных машин см. в разделе [создайте файл ответов](guarded-fabric-tenant-creates-shielding-data.md#create-an-answer-file).
 
## <a name="downloading-the-new-shieldingdataanswerfile-function"></a>Загрузка функции New-ShieldingDataAnswerFile

Вы можете получить **New-ShieldingDataAnswerFile** функции из [коллекции PowerShell](https://aka.ms/gftools). Если на компьютере установлено подключение к Интернету, это можно сделать с помощью PowerShell, выполнив следующую команду:

```powershell
Install-Module GuardedFabricTools -Repository PSGallery -MinimumVersion 1.0.0
```

`unattend.xml` Выходные данные можно упаковать в данные экранирования, а также дополнительные артефакты, чтобы его можно использовать для создания экранированных виртуальных машин на основе шаблонов.

В следующих разделах показано, как можно использовать для параметров функции `unattend.xml` файл, содержащий различные параметры:

- [Базовый Windows файл ответов](#basic-windows-answer-file)
- [Файл с помощью присоединения к домену ответов Windows](#windows-answer-file-with-domain-join)
- [Файл ответов Windows со статическими адресами IPv4](#windows-answer-file-with-static-ipv4-addresses)
- [Файл ответов Windows с помощью пользовательского языкового стандарта](#windows-answer-file-with-custom-locale)
- [Базовый файл ответов для Linux](#basic-linux-answer-file)

Вы также можете просмотреть [параметры функции](#function-parameters)далее в этом разделе.

## <a name="basic-windows-answer-file"></a>Базовый файл ответов Windows

Следующие команды создают файл ответов Windows, который просто устанавливает пароль учетной записи администратора и имя узла.
Сетевым адаптерам виртуальной Машины будет использовать DHCP для получения IP-адресов, а не виртуальная машина будет присоединен к домену Active Directory.
При появлении предложения ввести учетные данные администратора, укажите желаемое имя пользователя и пароль.
Используйте для имени пользователя «Администратор», если вы хотите настроить встроенной учетной записи администратора.

```powershell
$adminCred = Get-Credential -Prompt "Local administrator account"

New-ShieldingDataAnswerFile -Path '.\ShieldedVMAnswerFile.xml' -AdminCredentials $adminCred
```

## <a name="windows-answer-file-with-domain-join"></a>Файл с помощью присоединения к домену ответов Windows

Следующие команды создают файл ответов Windows, который присоединяет экранированной виртуальной Машины к домену Active Directory.
Сетевым адаптерам виртуальной Машины будет использовать DHCP для получения IP-адресов.

Первый запрос учетных данных будет запрашивать данные учетной записи локального администратора.
Используйте для имени пользователя «Администратор», если вы хотите настроить встроенной учетной записи администратора.

Второй запрос учетных данных будет запрашивать учетные данные, имеющие право на присоединение компьютера к домену Active Directory.

Не забудьте изменить значение «-DomainName» параметра на полное доменное имя домена Active Directory.

```powershell
$adminCred = Get-Credential -Prompt "Local administrator account"
$domainCred = Get-Credential -Prompt "Domain join credentials"

New-ShieldingDataAnswerFile -Path '.\ShieldedVMAnswerFile.xml' -AdminCredentials $adminCred -DomainName 'my.contoso.com' -DomainJoinCredentials $domainCred
```
## <a name="windows-answer-file-with-static-ipv4-addresses"></a>Файл ответов Windows со статическими адресами IPv4

Следующие команды создают файл ответов Windows, использующего статические IP-адреса, предоставляемые диспетчер структуры, такие как System Center Virtual Machine Manager во время развертывания.

Virtual Machine Manager предоставляет три компонента статический IP-адрес, используя пул IP-адресов: IPv4-адрес, IPv6-адрес, адрес шлюза и DNS-адрес. Если требуется, чтобы любые дополнительные поля, включаемые или требуется пользовательская настройка сети, необходимо будет вручную изменить файл ответов, созданный с помощью скрипта.

Далее на снимках экрана показано пулы IP-адресов, которые можно настроить в Virtual Machine Manager. Эти пулы необходимы в том случае, если вы хотите использовать статический IP-адрес.

В настоящее время функция поддерживает только один DNS-сервер. Вот, что параметры DNS выглядит следующим образом:

![Настройка DNS-сервера с помощью пула статических IP-адресов](../media/Guarded-Fabric-Shielded-VM/guarded-host-unattend-static-ip-address-pool-dns-settings.png)

Вот, как будет выглядеть итоги для создания пула IP-адреса. Иными словами необходимо иметь только один сетевой маршрут, один шлюз и один DNS-сервер - и необходимо указать IP-адрес.

![Сводка по созданию пула статических IP-адрес](../media/Guarded-Fabric-Shielded-VM/guarded-host-unattend-static-ip-address-pool-summary.png)

Необходимо настроить сетевой адаптер для виртуальной машины. На следующем рисунке показан, где можно настроить эту конфигурацию и как переключиться статический IP-адрес.

![Настройте оборудование для использования статического IP-адреса](../media/Guarded-Fabric-Shielded-VM/guarded-host-unattend-static-ip-address-pool-network-adapter-settings.png)

Затем вы можете использовать `-StaticIPPool` параметр для включения статических элементов IP-адрес в файле ответов. Параметры `@IPAddr-1@`, `@NextHop-1-1@`, и `@DNSAddr-1-1@` в ответе файл затем заменяется реальные значения, заданные в Virtual Machine Manager во время развертывания.

```powershell
$adminCred = Get-Credential -Prompt "Local administrator account"

New-ShieldingDataAnswerFile -Path '.\ShieldedVMAnswerFile.xml' -AdminCredentials $adminCred -StaticIPPool IPv4Address
```

## <a name="windows-answer-file-with-a-custom-locale"></a>Файл ответов Windows с помощью пользовательского языкового стандарта

Следующие команды создают файл ответов Windows с помощью пользовательского языкового стандарта.

При появлении предложения ввести учетные данные администратора, укажите желаемое имя пользователя и пароль.
Используйте для имени пользователя «Администратор», если вы хотите настроить встроенной учетной записи администратора.

```powershell
$adminCred = Get-Credential -Prompt "Local administrator account"
$domainCred = Get-Credential -Prompt "Domain join credentials"

New-ShieldingDataAnswerFile -Path '.\ShieldedVMAnswerFile.xml' -AdminCredentials $adminCred -Locale es-ES
```

## <a name="basic-linux-answer-file"></a>Базовый файл ответов для Linux

Начиная с Windows Server версии 1709, можно запустить некоторые Linux гостевых ОС в экранированные виртуальные машины.
При использовании агента System Center Virtual Machine Manager Linux для уточнения этих виртуальных машинах, командлет New-ShieldingDataAnswerFile можно создать файлы совместимых ответов для него.

В файле ответов Linux обычно будет включать пароль пользователя root, корневой ключ SSH и при необходимости статические данные о пуле IP-адрес.
Замените путь к открытый ключ SSH перед запуском приведенный ниже сценарий.

```powershell
$rootPassword = Read-Host -Prompt "Root password" -AsSecureString

New-ShieldingDataAnswerFile -Path '.\ShieldedVMAnswerFile.xml' -RootPassword $rootPassword -RootSshKey '~\.ssh\id_rsa.pub'
```

## <a name="see-also"></a>См. также

- [Развернуть экранированные виртуальные машины](guarded-fabric-configuration-scenarios-for-shielded-vms-overview.md)
- [Защищенная структура и экранированные виртуальные машины](guarded-fabric-and-shielded-vms-top-node.md)
