---
title: Развертывание Windows Admin Center с высоким уровнем доступности
description: Развертывание Windows Admin Center с высоким уровнем доступности (Гонолулу проекта)
ms.technology: manage
ms.topic: article
author: jwwool
ms.author: jeffrew
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: a0062230dd3d9e9c52aa317f87e06b0e84507dc4
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59861065"
---
# <a name="deploy-windows-admin-center-with-high-availability"></a>Развертывание Windows Admin Center с высоким уровнем доступности

>Область применения. Windows Admin Center, предварительная версия Windows Admin Center

Вы можете развернуть Windows Admin Center в отказоустойчивом кластере для обеспечения высокой доступности для службы шлюза Windows Admin Center. Решение, представленное вполне решение активный / пассивный, где действует только один экземпляр Windows Admin Center. В случае сбоя одного из узлов в кластере Windows Admin Center корректно при сбое на другой узел, позволяя продолжить управление серверами в вашей среде без проблем. 

[Дополнительные сведения о других вариантах развертывания Windows Admin Center.](../plan/installation-options.md)

## <a name="prerequisites"></a>предварительные требования

- Отказоустойчивый кластер из двух или более узлов в Windows Server 2016 или 2019 г. [Дополнительные сведения о развертывании отказоустойчивого кластера](../../../failover-clustering/failover-clustering-overview.md).
- Кластер общего тома (CSV) для Windows Admin Center для хранения постоянных данных, доступную всем узлам в кластере. 10 ГБ, будет достаточно для CSV-файла.
- Скрипт развертывания высокого уровня доступности из [ZIP-файл Windows Admin Center высокого уровня ДОСТУПНОСТИ скрипт](https://aka.ms/WACHAScript). Скачайте ZIP-файл, содержащий сценарий на локальный компьютер и скопируйте скрипт при необходимости зависимости от указанных ниже инструкций.
- Рекомендуется, но это необязательно: подписанный сертификат PFX-файл и пароль. Не нужно установить сертификат на узлах кластера — сценарий сделает это за вас. Если не указан, сценарий установки создает самозаверяющий сертификат, срок действия которого истекает через 60 дней.

## <a name="install-windows-admin-center-on-a-failover-cluster"></a>Установка Windows Admin Center в отказоустойчивом кластере

1. Копировать ```Install-WindowsAdminCenterHA.ps1``` скрипт на узел в кластере. Загрузите или скопируйте MSI-файл Windows Admin Center на тот же узел.
2. Подключитесь к узлу с помощью протокола удаленного рабочего СТОЛА и запустите ```Install-WindowsAdminCenterHA.ps1``` сценарий из этого узла со следующими параметрами:
    - `-clusterStorage`: локальный путь общего тома кластера для хранения данных Windows Admin Center.
    - `-clientAccessPoint`: выберите имя, которое будет использоваться для доступа к Windows Admin Center. Например, если вы запустите скрипт с параметром `-clientAccessPoint contosoWindowsAdminCenter`, будет доступ к службе Windows Admin Center, посетив `https://contosoWindowsAdminCenter.<domain>.com`
    - `-staticAddress`. Необязательно. Один или несколько статических адресов для общей службы кластера. 
    - `-msiPath`. Путь к MSI-файл Windows Admin Center.
    - `-certPath`. Необязательно. Путь к PFX-файл сертификата.
    - `-certPassword`. Необязательный. Пароль для PFX-файла сертификата, указанный в SecureString `-certPath`
    - `-generateSslCert`. Необязательный. Если вы не хотите предоставить подписанный сертификат, включают этот флаг параметр, чтобы создать самозаверяющий сертификат. Обратите внимание на то, что сертификат с собственной подписью истечет через 60 дней.
    - `-portNumber`. Необязательный. Если не указать порт, через порт 443 (HTTPS) развертывания службы шлюза. Чтобы использовать другой порт указать в этом параметре. Обратите внимание, что если вы используете другой номер порта (что-либо, кроме порта 443), обращения к Windows Admin Center, перейдя к https://\<clientAccessPoint\>:\<порт\>.

> [!NOTE]
> ```Install-WindowsAdminCenterHA.ps1``` Скрипт поддерживает ```-WhatIf ``` и ```-Verbose``` параметров

### <a name="examples"></a>Примеры

#### <a name="install-with-a-signed-certificate"></a>Установка с использованием подписанного сертификата.

```powershell
$certPassword = Read-Host -AsSecureString
.\Install-WindowsAdminCenterHA.ps1 -clusterStorage "C:\ClusterStorage\Volume1" -clientAccessPoint "contoso-ha-gateway" -msiPath ".\WindowsAdminCenter.msi" -certPath "cert.pfx" -certPassword $certPassword -Verbose
```

#### <a name="install-with-a-self-signed-certificate"></a>Установка с использованием самозаверяющего сертификата.

```powershell
.\Install-WindowsAdminCenterHA.ps1 -clusterStorage "C:\ClusterStorage\Volume1" -clientAccessPoint "contoso-ha-gateway" -msiPath ".\WindowsAdminCenter.msi" -generateSslCert -Verbose
```

## <a name="update-an-existing-high-availability-installation"></a>Обновление существующей установки высокого уровня доступности

Используйте тот же ```Install-WindowsAdminCenterHA.ps1``` сценария для обновления развертывания высокого уровня ДОСТУПНОСТИ, не теряя данные подключения.

### <a name="update-to-a-new-version-of-windows-admin-center"></a>Обновление до новой версии Windows Admin Center

При выпуске новой версии Windows Admin Center, просто запустите ```Install-WindowsAdminCenterHA.ps1``` скрипт еще раз с единственным ```msiPath``` параметр:

```powershell
.\Install-WindowsAdminCenterHA.ps1 -msiPath '.\WindowsAdminCenter.msi' -Verbose
```

### <a name="update-the-certificate-used-by-windows-admin-center"></a>Обновить сертификат, используемый Windows Admin Center

Вы можете обновить сертификат, используемый при развертывании Windows Admin Center высокого уровня ДОСТУПНОСТИ в любое время, предоставляя новый сертификат PFX-файл и и пароль.

```powershell
$certPassword = Read-Host -AsSecureString
.\Install-WindowsAdminCenterHA.ps1 -certPath "cert.pfx" -certPassword $certPassword -Verbose
```

Также вы можете обновить сертификат в то же время, обновление платформы Windows Admin Center с помощью нового MSI-файла.

```powershell
$certPassword = Read-Host -AsSecureString
.\Install-WindowsAdminCenterHA.ps1 -msiPath ".\WindowsAdminCenter.msi" -certPath "cert.pfx" -certPassword $certPassword -Verbose
``` 

## <a name="uninstall"></a>Удалить

Чтобы удалить развертывание высокой ДОСТУПНОСТИ Windows Admin Center в отказоустойчивом кластере, передайте ```-Uninstall``` параметр ```Install-WindowsAdminCenterHA.ps1``` скрипта.

```powershell
.\Install-WindowsAdminCenterHA.ps1 -Uninstall -Verbose
```

## <a name="troubleshooting"></a>Устранение неполадок

Журналы сохраняются во временной папке CSV-файла (например, C:\ClusterStorage\Volume1\temp).