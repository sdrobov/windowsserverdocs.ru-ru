---
title: Развертывание шлюза Windows Admin Center в Azure
description: Развертывание шлюза Windows Admin Center в Azure
ms.technology: manage
ms.topic: article
author: jwwool
ms.author: jeffrew
ms.date: 04/12/2019
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: af766c2e0502d9fe633cae42d999db5cbffc32c8
ms.sourcegitcommit: f1edfc6525e09dd116b106293f9260123a94de0c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "9296999"
---
# Развертывание Windows Admin Center в Azure

## Развертывание с помощью сценария

Вы можете скачать [WACAzVM.ps1 развертывание](https://aka.ms/deploy-wacazvm) , которое будет выполняться из [Оболочки облаке Azure](https://shell.azure.com) для настройки шлюз Windows Admin Center в Azure. Этот сценарий можно создать всего среды, в том числе группы ресурсов.

[Перейти к шаги развертывания вручную](#deploy-manually-on-an-existing-azure-virtual-machine)

### Что вам понадобится

* Настройка учетной записи в [Оболочке облака Azure](https://shell.azure.com). Если это первый раз с помощью облачных оболочки, вам будет задано связать или создать учетную запись службы хранилища Azure с оболочкой облака.
* В оболочке **PowerShell** облака перейдите к домашнему каталогу: ```PS Azure:\> cd ~```
* Для отправки ```Deploy-WACAzVM.ps1``` файл, перетащите с локального компьютера в любом месте в диалоговом окне облачных оболочки.

Если указать свой собственный сертификат:

* Отправка сертификата в [Хранилище ключей Azure](https://docs.microsoft.com/en-us/azure/key-vault/key-vault-whatis). Во-первых создайте основные хранилище на портале Azure, а затем отправить сертификат в хранилище ключей. Кроме того можно использовать портал Azure для создания сертификата для вас.

### Параметры сценария

* **ResourceGroupName** - [строка] Указывает имя группы ресурсов, где будут создаваться виртуальной Машины.

* **Имя** - [строка] Указывает имя виртуальной Машины.

* **Учетные данные** - [PSCredential] указывает учетные данные для виртуальной Машины.

* **MsiPath** - [строка] указывает локальный путь к Windows Admin Center MSI при развертывании Windows Admin Center на виртуальной Машине существующего. По умолчанию используется версия из http://aka.ms/WACDownload Если этот параметр пропущен.

* **VaultName** - [строка] Указывает имя ключа хранилище с сертификатом.

* **CertName** - [строка] Указывает имя сертификата, который будет использоваться для установки MSI.

* **GenerateSslCert** - [Switch] — значение True, если MSI нужно создать собственный подписанные ssl-сертификат.

* **Номер_порта** - [int] указывает номер порта ssl для службы Windows Admin Center. По умолчанию 443, если не указано.

* **OpenPorts** - [int []] указывает открытые порты для виртуальной Машины.

* **Расположение** - [строка] указывает виртуальной машины.

* **Размер** - [строка] размер виртуальной машины. По умолчанию «Standard_DS1_v2», если не указано.

* **Изображения** — [строка] указывает образ виртуальной машины. По умолчанию «Win2016Datacenter», если не указано.

* **VirtualNetworkName** - [строка] Указывает имя виртуальной сети для виртуальной Машины.

* **SubnetName** - [строка] Указывает имя подсети для виртуальной Машины.

* **SecurityGroupName** - [строка] Указывает имя группы безопасности для виртуальной Машины.

* **PublicIpAddressName** - [строка] Указывает имя общий IP-адрес для виртуальной Машины.

* **InstallWACOnly** - [Switch] задано значение True, если WAC должны быть установлены на существующие виртуальных Машин Azure.

Существует 2 варианта различных MSI для развертывания и сертификат, используемый для установки MSI. MSI-ФАЙЛ можно загрузить либо из aka.ms/WACDownload или, если развертывание существующей виртуальной Машины, можно предоставить filepath MSI локально на виртуальной Машине. Сертификат можно найти в любом хранилище ключей Azure или самозаверяющий сертификат будет создан, MSI-ФАЙЛУ.

### Примеры сценариев

Во-первых Определите общие переменные, необходимые для параметров сценария.

```PowerShell
$ResourceGroupName = "wac-rg1" 
$VirtualNetworkName = "wac-vnet"
$SecurityGroupName = "wac-nsg"
$SubnetName = "wac-subnet"
$VaultName = "wac-key-vault"
$CertName = "wac-cert"
$Location = "westus"
$PublicIpAddressName = "wac-public-ip"
$Size = "Standard_D4s_v3"
$Image = "Win2016Datacenter"
$Credential = Get-Credential
```

#### Пример 1: Используйте сценарий развертывания шлюза WAC в новую виртуальную Машину в новой виртуальной сети и ресурсов группы. С помощью MSI-ФАЙЛ из aka.ms/WACDownload и самозаверяющий сертификат из MSI-ФАЙЛУ.

```PowerShell
$scriptParams = @{
    ResourceGroupName = $ResourceGroupName
    Name = "wac-vm1"
    Credential = $Credential
    VirtualNetworkName = $VirtualNetworkName
    SubnetName = $SubnetName
    GenerateSslCert = $true
}
./Deploy-WACAzVM.ps1 @scriptParams
```

#### Пример 2: Так же, как #1, но с помощью сертификата в хранилище ключей Azure.

```PowerShell
$scriptParams = @{
    ResourceGroupName = $ResourceGroupName
    Name = "wac-vm2"
    Credential = $Credential
    VirtualNetworkName = $VirtualNetworkName
    SubnetName = $SubnetName
    VaultName = $VaultName
    CertName = $CertName
}
./Deploy-WACAzVM.ps1 @scriptParams
```

#### Пример 3: С помощью локального MSI на виртуальной Машине существующего развертывания WAC.

```PowerShell
$MsiPath = "C:\Users\<username>\Downloads\WindowsAdminCenter<version>.msi"
$scriptParams = @{
    ResourceGroupName = $ResourceGroupName
    Name = "wac-vm3"
    Credential = $Credential
    MsiPath = $MsiPath
    InstallWACOnly = $true
    GenerateSslCert = $true
}
./Deploy-WACAzVM.ps1 @scriptParams
```

### Требования для виртуальной Машины, работает шлюз Windows Admin Center

Должен быть открыт порт 443 (HTTPS).
Используя те же самые переменные, определенного для письма, можно использовать приведенный ниже код в оболочке облаке Azure для обновления в группе безопасности сети:

```powershell
$nsg = Get-AzNetworkSecurityGroup -Name $SecurityGroupName -ResourceGroupName $ResourceGroupName
$newNSG = Add-AzNetworkSecurityRuleConfig -NetworkSecurityGroup $nsg -Name ssl-rule -Description "Allow SSL" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 443
Set-AzNetworkSecurityGroup -NetworkSecurityGroup $newNSG
```

### Требования для управляемых Azure Виртуальной машины

Порт 5985 (WinRM по протоколу HTTP) должен быть открытым и иметь активным.
Приведенный ниже код в оболочке облака Azure можно использовать для обновления управляемым узлам. ```$ResourceGroupName``` и ```$Name``` использовать те же самые переменные в качестве сценарий развертывания, но вам необходимо использовать ```$Credential``` относящиеся к виртуальной Машине вы управляете.

```powershell
Enable-AzVMPSRemoting -ResourceGroupName $ResourceGroupName -Name $Name
Invoke-AzVMCommand -ResourceGroupName $ResourceGroupName -Name $Name -ScriptBlock {Set-NetFirewallRule -Name WINRM-HTTP-In-TCP-PUBLIC -RemoteAddress Any} -Credential $Credential
Invoke-AzVMCommand -ResourceGroupName $ResourceGroupName -Name $Name -ScriptBlock {winrm create winrm/config/Listener?Address=*+Transport=HTTP} -Credential $Credential
```

## Развертывание вручную в существующей виртуальной машине Azure

Перед установкой Windows Admin Center на нужную шлюз виртуальной Машины, установить сертификат SSL для HTTPS взаимодействия, или вы можете использовать самозаверяющий сертификат, созданный Windows Admin Center. Тем не менее вы получите предупреждение, при попытке подключения в браузере, если выбран последний вариант. Это предупреждение в Edge можно обойти, щелкнув **> сведений перейдите веб-страницу** или в Chrome, выбрав **расширенных > перейти к [веб-страницы]**. Мы рекомендуем только использование самозаверяющих сертификатов для тестовой среды.

> [!NOTE]
> Эти инструкции предназначены для установки в Windows Server с возможностями рабочего стола, не в установке Server Core. 

1. [Скачайте Windows Admin Center](https://aka.ms/windowsadmincenter) на локальном компьютере.

2. Удаленного рабочего стола подключение к виртуальной Машине, а затем скопировать MSI-ФАЙЛ с локального компьютера и вставить в виртуальной Машине.

3. Дважды щелкните MSI, чтобы начать установку и следуйте инструкциям в мастере. Следует учитывать следующее:

   - По умолчанию установщик использует Рекомендуемый порт 443 (HTTPS). Если вы хотите выбрать другой порт, обратите внимание, что вам нужно открыть порт брандмауэра, а также. 

   - Если вы уже установили SSL-сертификата на виртуальной Машине, убедитесь, выберите соответствующий вариант и введите отпечаток.

4. Запустите службу Windows Admin Center (запуск Center/sme.exe администратора файлов или Windows C: и программам)

[Дополнительные сведения о развертывании Windows Admin Center.](../deploy/install.md)

### Настройте шлюз виртуальной Машины для включения доступа к порту HTTPS. 

1. Перейдите к виртуальные Машины на портале Azure и выберите **сеть**. 

2. Выберите **Добавление правила порта для входящего трафика** и **HTTPS** в **службе**. 

> [!NOTE]
> Если вы выбрали порт 443 по умолчанию, выберите **пользовательские** под службы и введите порт, который вы выбрали в шаге 3, под **диапазоны портов**. 

### Доступ к шлюз Windows Admin Center, установленных на виртуальной Машине Azure

На этом этапе вы сможете получить доступ к Windows Admin Center из современных браузера (Edge или Chrome) на локальном компьютере, перейдя на DNS-имя вашего шлюза виртуальной Машины. 

> [!NOTE]
> Если вы выбрали порт 443, можно получить доступ к Windows Admin Center, перейдя на имя вашей VM\>:\<custom port\> https://\<DNS

При попытке доступа к Windows Admin Center, браузер будет запрашивать учетные данные для доступа к виртуальной машине, на котором установлена Windows Admin Center. Здесь необходимо ввести учетные данные, которые находятся в локальные пользователи или группы локальных администраторов на виртуальной машине. 

Чтобы добавить другие виртуальные машины в подсоединена, убедитесь, что WinRM выполняется на целевом виртуальных машин, выполнив следующие в PowerShell или командную строку на целевом виртуальной Машины: `winrm quickconfig`

Если вы еще не присоединенный к домену виртуальной Машине Azure, виртуальная машина ведет себя как сервера в рабочей группе, поэтому необходимо убедиться, что вы учитывать [с помощью Windows Admin Center в рабочей группе](../support/troubleshooting.md#using-windows-admin-center-in-a-workgroup).