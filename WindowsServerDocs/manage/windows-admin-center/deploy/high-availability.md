---
title: Развертывание центра администрирования Windows с высоким уровнем доступности
description: Развертывание центра администрирования Windows с высоким уровнем доступности (проект Хонолулу)
ms.technology: manage
ms.topic: article
author: jwwool
ms.author: jeffrew
ms.localizationpriority: medium
ms.prod: windows-server
ms.openlocfilehash: 6ae7bd9ed7aee5835ac1f53b9e10879ad8824f52
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71406943"
---
# <a name="deploy-windows-admin-center-with-high-availability"></a>Развертывание центра администрирования Windows с высоким уровнем доступности

>Относится к Windows Admin Center, ознакомительной версии Windows Admin Center

Центр администрирования Windows можно развернуть в отказоустойчивом кластере, чтобы обеспечить высокий уровень доступности для службы шлюза центра администрирования Windows. Предоставленное решение является активным-пассивным решением, в котором активен только один экземпляр центра администрирования Windows. В случае сбоя одного из узлов в кластере центр администрирования Windows корректно переключается на другой узел, позволяя без проблем управлять серверами в среде. 

[Узнайте о других вариантах развертывания центра администрирования Windows.](../plan/installation-options.md)

## <a name="prerequisites"></a>Предварительные условия

- Отказоустойчивый кластер из двух или более узлов на Windows Server 2016 или 2019. Дополнительные [сведения о развертывании отказоустойчивого кластера](../../../failover-clustering/failover-clustering-overview.md).
- Общий том кластера (CSV) для центра администрирования Windows для хранения постоянных данных, доступных для всех узлов в кластере. для CSV-файла будет достаточно 10 ГБ.
- Скрипт развертывания высокого уровня доступности из [ZIP-файла сценария высокой надежности Windows Admin Center](https://aka.ms/WACHAScript). Скачайте ZIP-файл, содержащий сценарий, на локальный компьютер, а затем скопируйте сценарий по мере необходимости в соответствии с приведенными ниже инструкциями.
- Рекомендуется, но необязательно: подписанный сертификат. pfx & пароль. Вам не нужно устанавливать сертификат на узлах кластера. сценарий сделает это самостоятельно. Если он не указан, сценарий установки создает самозаверяющий сертификат, срок действия которого истекает через 60 дней.

## <a name="install-windows-admin-center-on-a-failover-cluster"></a>Установка центра администрирования Windows в отказоустойчивом кластере

1. Скопируйте сценарий ```Install-WindowsAdminCenterHA.ps1``` на узел в кластере. Скачайте или скопируйте файл Windows Admin Center. msi на тот же узел.
2. Подключитесь к узлу через RDP и запустите сценарий ```Install-WindowsAdminCenterHA.ps1``` из этого узла со следующими параметрами:
    - `-clusterStorage`: локальный путь общий том кластера для хранения данных центра администрирования Windows.
    - `-clientAccessPoint`. Выберите имя, которое будет использоваться для доступа к центру администрирования Windows. Например, если запустить скрипт с параметром `-clientAccessPoint contosoWindowsAdminCenter`, вы получите доступ к службе центра администрирования Windows, посетив `https://contosoWindowsAdminCenter.<domain>.com`
    - `-staticAddress`: необязательный. Один или несколько статических адресов для универсальной службы кластера. 
    - `-msiPath`: путь к MSI файл центра администрирования Windows.
    - `-certPath`: необязательный. Путь к PFX-файлу сертификата.
    - `-certPassword`: необязательный. Пароль SecureString для файла Certificate. pfx, предоставленный в `-certPath`
    - `-generateSslCert`: необязательный. Если вы не хотите предоставлять подписанный сертификат, включите этот флаг параметра, чтобы создать самозаверяющий сертификат. Обратите внимание, что срок действия самозаверяющего сертификата истекает через 60 дней.
    - `-portNumber`: необязательный. Если порт не указан, служба шлюза развертывается на порте 443 (HTTPS). Чтобы использовать другой порт, укажите в этом параметре. Обратите внимание, что при использовании настраиваемого порта (что еще не 443) вы можете получить доступ к центру администрирования Windows, перейдя в https://\<Клиентакцесспоинт\>:\<порт\>.

> [!NOTE]
> Скрипт ```Install-WindowsAdminCenterHA.ps1``` поддерживает параметры ```-WhatIf ``` и ```-Verbose```

### <a name="examples"></a>Примеры.

#### <a name="install-with-a-signed-certificate"></a>Установите с подписанным сертификатом:

```powershell
$certPassword = Read-Host -AsSecureString
.\Install-WindowsAdminCenterHA.ps1 -clusterStorage "C:\ClusterStorage\Volume1" -clientAccessPoint "contoso-ha-gateway" -msiPath ".\WindowsAdminCenter.msi" -certPath "cert.pfx" -certPassword $certPassword -Verbose
```

#### <a name="install-with-a-self-signed-certificate"></a>Установите с самозаверяющим сертификатом:

```powershell
.\Install-WindowsAdminCenterHA.ps1 -clusterStorage "C:\ClusterStorage\Volume1" -clientAccessPoint "contoso-ha-gateway" -msiPath ".\WindowsAdminCenter.msi" -generateSslCert -Verbose
```

## <a name="update-an-existing-high-availability-installation"></a>Обновление существующей установки высокого уровня доступности

Используйте тот же сценарий ```Install-WindowsAdminCenterHA.ps1```, чтобы обновить развертывание с высоким уровнем доступности без потери данных подключения.

### <a name="update-to-a-new-version-of-windows-admin-center"></a>Обновление до новой версии центра администрирования Windows

При выпуске новой версии центра администрирования Windows просто запустите сценарий ```Install-WindowsAdminCenterHA.ps1```, используя только параметр ```msiPath```:

```powershell
.\Install-WindowsAdminCenterHA.ps1 -msiPath '.\WindowsAdminCenter.msi' -Verbose
```

### <a name="update-the-certificate-used-by-windows-admin-center"></a>Обновление сертификата, используемого центром администрирования Windows

Вы можете в любое время обновить сертификат, используемый центром администрирования Windows с высоким уровнем доступности, указав PFX-файл и пароль нового сертификата.

```powershell
$certPassword = Read-Host -AsSecureString
.\Install-WindowsAdminCenterHA.ps1 -certPath "cert.pfx" -certPassword $certPassword -Verbose
```

Вы также можете обновить сертификат одновременно с новым MSI-файлом платформы центра администрирования Windows.

```powershell
$certPassword = Read-Host -AsSecureString
.\Install-WindowsAdminCenterHA.ps1 -msiPath ".\WindowsAdminCenter.msi" -certPath "cert.pfx" -certPassword $certPassword -Verbose
``` 

## <a name="uninstall"></a>Удалить

Чтобы удалить развертывание с высоким уровнем доступности центра администрирования Windows из отказоустойчивого кластера, передайте в скрипт ```Install-WindowsAdminCenterHA.ps1``` параметр ```-Uninstall```.

```powershell
.\Install-WindowsAdminCenterHA.ps1 -Uninstall -Verbose
```

## <a name="troubleshooting"></a>Поиск и устранение неисправностей

Журналы сохраняются во временной папке в CSV-файле (например, C:\ClusterStorage\Volume1\temp).