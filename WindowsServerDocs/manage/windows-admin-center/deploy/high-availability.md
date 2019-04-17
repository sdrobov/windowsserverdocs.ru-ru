---
title: Развертывание Windows Admin Center с высокой доступности
description: Развертывание Windows Admin Center с высокой доступности (проект Honolulu)
ms.technology: manage
ms.topic: article
author: jwwool
ms.author: jeffrew
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: a0062230dd3d9e9c52aa317f87e06b0e84507dc4
ms.sourcegitcommit: 802a7bd537cab22893abb7e6657c4be90346ef88
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "9025036"
---
# Развертывание Windows Admin Center с высокой доступности

>Относится к: Windows Admin Center, ознакомительная версия Windows Admin Center

Вы можете развернуть Windows Admin Center в отказоустойчивом кластере для обеспечения высокой доступности для вашей службы шлюз Windows Admin Center. Решение, представленное активный — пассивный решение —, где действует только один экземпляр Windows Admin Center. В случае сбоя одного из узлов кластера Windows Admin Center корректно при сбое на другой узел приступить к ее легко управления серверами в своей среде. 

[Сведения о других вариантов развертывания Windows Admin Center.](../plan/installation-options.md)

## Необходимые условия

- Отказоустойчивый кластер 2 или более узлов в Windows Server 2016 или 2019 г. [Подробнее о развертывании отказоустойчивого кластера](../../../failover-clustering/failover-clustering-overview.md).
- Общего тома кластера (CSV для Windows Admin Center для хранения постоянных данных, который может осуществляться из всех узлов в кластере). 10 ГБ будет достаточно для вашего CSV-файла.
- Сценарий развертывания высокого уровня доступности из [Windows Admin Center высокой ДОСТУПНОСТИ сценарий ZIP-файл](https://aka.ms/WACHAScript). Скачать ZIP-файл, содержащий скрипт на локальном компьютере и скопируйте сценарий при необходимости основании приведенным ниже рекомендациям.
- Рекомендуется, но необязательно: пароль & сертификат PFX-файл. Вам не нужно уже установлен сертификат на узлах кластера — сценарий сделает это за вас. Если вы не используете его, сценарий установки создает самозаверяющий сертификат, который истекает через 60 дней.

## Установка Windows Admin Center в отказоустойчивом кластере

1. Скопируйте ```Install-WindowsAdminCenterHA.ps1``` сценарий для узла в кластере. Загрузите или скопировать MSI-файл Windows Admin Center в том же узле.
2. Подключения к узлу с помощью протокола удаленного рабочего СТОЛА и выполнения ```Install-WindowsAdminCenterHA.ps1``` сценарий из этого узла со следующими параметрами:
    - `-clusterStorage`: локальный путь общего тома кластера для хранения данных Windows Admin Center.
    - `-clientAccessPoint`: выберите имя, которое будет использоваться для доступа к Windows Admin Center. Например, при запуске сценария с помощью параметра `-clientAccessPoint contosoWindowsAdminCenter`, будут получать доступ к службе Windows Admin Center, посетив страницу `https://contosoWindowsAdminCenter.<domain>.com`
    - `-staticAddress`: Необязательно. Один или несколько статические адреса для общей службы в кластере. 
    - `-msiPath`: Путь к файлу .msi Windows Admin Center.
    - `-certPath`: Необязательно. Путь для сертификата PFX-файла.
    - `-certPassword`: Необязательно. SecureString пароль для сертификата PFX-файл, приведенные в разделе `-certPath`
    - `-generateSslCert`: Необязательно. Если вы не хотите предоставить сертификат, включают этот флаг параметр, чтобы создать самозаверяющий сертификат. Обратите внимание, что самозаверяющего сертификата истекает через 60 дней.
    - `-portNumber`: Необязательно. Если не указать порт, служба шлюза развертывается на порт 443 (HTTPS). Для использования в этом параметре указать другой порт. Обратите внимание, что если вы используете пользовательский порт (никаких действий, кроме 443), будет доступ к Windows Admin Center последовательно выбрав пункты https://\<clientAccessPoint\>:\<port\>.

> [!NOTE]
> ```Install-WindowsAdminCenterHA.ps1``` Сценарий поддерживает ```-WhatIf ``` и ```-Verbose``` параметров

### Примеры:

#### Установка подписанные сертификатом.

```powershell
$certPassword = Read-Host -AsSecureString
.\Install-WindowsAdminCenterHA.ps1 -clusterStorage "C:\ClusterStorage\Volume1" -clientAccessPoint "contoso-ha-gateway" -msiPath ".\WindowsAdminCenter.msi" -certPath "cert.pfx" -certPassword $certPassword -Verbose
```

#### Установка с помощью самозаверяющего сертификата.

```powershell
.\Install-WindowsAdminCenterHA.ps1 -clusterStorage "C:\ClusterStorage\Volume1" -clientAccessPoint "contoso-ha-gateway" -msiPath ".\WindowsAdminCenter.msi" -generateSslCert -Verbose
```

## Обновить существующую установку высокого уровня доступности

Используйте тот же идентификатор ```Install-WindowsAdminCenterHA.ps1``` сценарий для обновления развертывания высокой ДОСТУПНОСТИ, без потери данных подключения.

### Обновление до более новой версии Windows Admin Center

При выпуске новой версии Windows Admin Center просто запустить ```Install-WindowsAdminCenterHA.ps1``` сценарий повторно с единственным ```msiPath``` параметр:

```powershell
.\Install-WindowsAdminCenterHA.ps1 -msiPath '.\WindowsAdminCenter.msi' -Verbose
```

### Обновить сертификат, используемый Windows Admin Center

Вы можете обновить сертификат, используемый счет развертывания Windows Admin Center в любое время, предоставляя нового сертификата PFX-файл и и пароль.

```powershell
$certPassword = Read-Host -AsSecureString
.\Install-WindowsAdminCenterHA.ps1 -certPath "cert.pfx" -certPassword $certPassword -Verbose
```

Можно также может обновить сертификат в то же время обновления платформы Windows Admin Center с помощью нового файла .msi.

```powershell
$certPassword = Read-Host -AsSecureString
.\Install-WindowsAdminCenterHA.ps1 -msiPath ".\WindowsAdminCenter.msi" -certPath "cert.pfx" -certPassword $certPassword -Verbose
``` 

## Удалить

Для удаления высокой ДОСТУПНОСТИ развертывания Windows Admin Center из отказоустойчивого кластера, передайте ```-Uninstall``` параметр ```Install-WindowsAdminCenterHA.ps1``` сценария.

```powershell
.\Install-WindowsAdminCenterHA.ps1 -Uninstall -Verbose
```

## Устранение неполадок

Журналы сохраняются в папке temp CSV-файлов (например, C:\ClusterStorage\Volume1\temp).