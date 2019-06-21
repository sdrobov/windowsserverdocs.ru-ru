---
title: Развертывание шлюза Windows Admin Center в Azure
description: Как развернуть шлюз Windows Admin Center в Azure
ms.technology: manage
ms.topic: article
author: jwwool
ms.author: jeffrew
ms.date: 04/12/2019
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: a3fa1838096d910505faf9a2c5bd819b3a256fe2
ms.sourcegitcommit: afb0602767de64a76aaf9ce6a60d2f0e78efb78b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/20/2019
ms.locfileid: "67280413"
---
# <a name="deploy-windows-admin-center-in-azure"></a>Развертывание Windows Admin Center в Azure

## <a name="deploy-using-script"></a>Развертывание с помощью скрипта

Вы можете скачать [развернуть WACAzVM.ps1](https://aka.ms/deploy-wacazvm) которого запускается из [Azure Cloud Shell](https://shell.azure.com) для настройки шлюза Windows Admin Center в Azure. Этот скрипт может создать всю среду, включая группу ресурсов.

[Перейти к развертывания вручную](#deploy-manually-on-an-existing-azure-virtual-machine)

### <a name="prerequisites"></a>предварительные требования

* Настройка учетной записи в [Azure Cloud Shell](https://shell.azure.com). Если вы впервые используете Cloud Shell, вам нужно будет связать или создать учетную запись хранения Azure с помощью Cloud Shell.
* В **PowerShell** Cloud Shell, перейдите в корневой каталог: ```PS Azure:\> cd ~```
* Чтобы отправить ```Deploy-WACAzVM.ps1``` файл, перетащите и поместите его на локальном компьютере в любое место в окно Cloud Shell.

При указании собственный сертификат:

* Передайте сертификат, который [Azure Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-whatis). Во-первых создайте хранилище ключей на портале Azure, а затем отправьте сертификат в хранилище ключей. Кроме того можно использовать портал Azure для создания сертификата для вас.

### <a name="script-parameters"></a>Параметры сценария

* **ResourceGroupName** -[String] Указывает имя группы ресурсов, в котором будет создана виртуальная машина.

* **Имя** -[String] Указывает имя виртуальной машины.

* **Учетные данные** -[PSCredential] Задает учетные данные для виртуальной Машины.

* **MsiPath** -[String] указывает локальный путь к MSI-ФАЙЛ Windows Admin Center при развертывании Windows Admin Center на существующей виртуальной Машины. По умолчанию используется версия от http://aka.ms/WACDownload Если не указано.

* **VaultName** -[String] Указывает имя хранилища ключей, содержащего сертификат.

* **CertName** -[String] Указывает имя сертификата, используемого для установки MSI.

* **GenerateSslCert** — [параметр] значение True, если MSI-ФАЙЛ должен создать собственный подписанного SSL-сертификат.

* **PortNumber** -[int] указывает номер порта ssl для службы Windows Admin Center. По умолчанию 443, если не указано.

* **OpenPorts** -[int []] указывает открытых портов для виртуальной Машины.

* **Расположение** -[String] Указывает расположение виртуальной машины.

* **Размер** -[String] указывает размер виртуальной машины. По умолчанию «Standard_DS1_v2», если не указано.

* **Изображение** -[String] указывает образ виртуальной машины. По умолчанию «Win2016Datacenter», если не указано.

* **VirtualNetworkName** -[String] Указывает имя виртуальной сети для виртуальной Машины.

* **SubnetName** -[String] Указывает имя подсети для виртуальной Машины.

* **SecurityGroupName** -[String] Указывает имя группы безопасности для виртуальной Машины.

* **PublicIpAddressName** -[String] Указывает имя общедоступного IP-адреса для виртуальной Машины.

* **InstallWACOnly** — [параметр] значение True, если WAC должен быть установлен на существующей виртуальной Машине Azure.

Существует 2 различных варианта MSI-ФАЙЛ для развертывания и сертификат, используемый для установки MSI. MSI-ФАЙЛ можно скачать либо aka.ms/WACDownload или, если развертывание выполняется в существующей виртуальной Машины, можно указать путь к файлу MSI локально на виртуальной Машине. Сертификат можно найти в любом хранилище ключей Azure, или самозаверяющий сертификат будет сформирована методом MSI-ФАЙЛ.

### <a name="script-examples"></a>Примеры сценариев

Во-первых Определите общие переменные, необходимый для параметров сценария.

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

#### <a name="example-1-use-the-script-to-deploy-wac-gateway-on-a-new-vm-in-a-new-virtual-network-and-resource-group-use-the-msi-from-akamswacdownload-and-a-self-signed-cert-from-the-msi"></a>Пример 1: Используйте сценарий для развертывания шлюза WAC на новую виртуальную Машину в новой виртуальной сети и группе ресурсов. С помощью MSI-ФАЙЛ из aka.ms/WACDownload и самозаверяющий сертификат из MSI-ФАЙЛ.

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

#### <a name="example-2-same-as-1-but-using-a-certificate-from-azure-key-vault"></a>Пример 2: Совпадает со значением #1, но с помощью сертификата из хранилища ключей Azure.

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

#### <a name="example-3-using-a-local-msi-on-an-existing-vm-to-deploy-wac"></a>Пример 3. С помощью локального MSI на существующую виртуальную Машину для развертывания WAC.

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

### <a name="requirements-for-vm-running-the-windows-admin-center-gateway"></a>Требования для виртуальной Машины под управлением Windows Admin Center шлюза

Должен быть открыт порт 443 (HTTPS).
Используя переменные, определенные для скрипта, можно использовать приведенный ниже код в Azure Cloud Shell для обновления группы безопасности сети:

```powershell
$nsg = Get-AzNetworkSecurityGroup -Name $SecurityGroupName -ResourceGroupName $ResourceGroupName
$newNSG = Add-AzNetworkSecurityRuleConfig -NetworkSecurityGroup $nsg -Name ssl-rule -Description "Allow SSL" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 443
Set-AzNetworkSecurityGroup -NetworkSecurityGroup $newNSG
```

### <a name="requirements-for-managed-azure-vms"></a>Требования к управляемой виртуальной Машины Azure

Порт 5985 (WinRM по протоколу HTTP) должен быть открытым и иметь ли активные прослушиватели.
Приведенный ниже код в Azure Cloud Shell можно использовать для обновления управляемых узлов. ```$ResourceGroupName``` и ```$Name``` использовать переменные, как скрипт развертывания, но необходимо будет использовать ```$Credential``` относящиеся к виртуальной Машине вы управляете.

```powershell
Enable-AzVMPSRemoting -ResourceGroupName $ResourceGroupName -Name $Name
Invoke-AzVMCommand -ResourceGroupName $ResourceGroupName -Name $Name -ScriptBlock {Set-NetFirewallRule -Name WINRM-HTTP-In-TCP-PUBLIC -RemoteAddress Any} -Credential $Credential
Invoke-AzVMCommand -ResourceGroupName $ResourceGroupName -Name $Name -ScriptBlock {winrm create winrm/config/Listener?Address=*+Transport=HTTP} -Credential $Credential
```

## <a name="deploy-manually-on-an-existing-azure-virtual-machine"></a>Развертывание вручную на существующей виртуальной машине Azure

Перед установкой Windows Admin Center на требуемой виртуальной Машины шлюза, установить SSL-сертификат, используемый для подключения по протоколу HTTPS, или вы можете использовать самозаверяющий сертификат, созданный Windows Admin Center. Тем не менее вы получите предупреждение при попытке подключения из браузера, если вы выберите второй вариант. Вы можете обойти это предупреждение в Edge, нажав кнопку **сведения > перейдите веб-страницу** или в браузере Chrome, выбрав **Дополнительно > продолжить [веб-страницу]** . Мы рекомендуем использовать самозаверяющие сертификаты для тестовых сред.

> [!NOTE]
> Эти инструкции предназначены для установки на Windows Server с рабочим столом, не в установке основных серверных компонентов. 

1. [Загрузка Windows Admin Center](https://aka.ms/windowsadmincenter) на локальный компьютер.

2. Установить удаленное подключение рабочего стола к виртуальной Машине, а затем скопируйте MSI-ФАЙЛ с локального компьютера и вставьте в виртуальной Машине.

3. Дважды щелкните MSI-ФАЙЛ, чтобы начать установку и следуйте инструкциям в мастере. Необходимо учитывать следующее.

   - По умолчанию установщик использует Рекомендуемый порт 443 (HTTPS). Если вы хотите выбрать другой порт, обратите внимание, что вам нужно открыть порт в брандмауэре также. 

   - Если вы уже установили SSL-сертификата на виртуальной Машине, убедитесь, чтобы выбрать соответствующий параметр и ввести отпечаток.

4. Запустите службу Windows Admin Center (запустите Center/sme.exe администратора C:/Program файлы или Windows)

[Дополнительные сведения о развертывании Windows Admin Center.](../deploy/install.md)

### <a name="configure-the-gateway-vm-to-enable-https-port-access"></a>Настройка шлюза виртуальной Машины, чтобы включить доступ по протоколам HTTPS-порт: 

1. Перейдите к виртуальной Машине в Azure, портала и выберите **сети**. 

2. Выберите **добавить правило входящего порта** и выберите **HTTPS** под **службы**. 

> [!NOTE]
> Если вы выбрали порт, отличный от 443 по умолчанию, выберите **Custom** в службе и укажите порт, выбранный на шаге 3 в разделе **порта диапазоны**. 

### <a name="accessing-a-windows-admin-center-gateway-installed-on-an-azure-vm"></a>Доступ к шлюзу Windows Admin Center, установленному на виртуальной Машины Azure

На этом этапе можно будет получить доступ к Windows Admin Center из современных браузерах (Edge или Chrome) на локальном компьютере, перейдя к DNS-имя шлюза виртуальной Машины. 

> [!NOTE]
> Если вы выбрали порт, отличный от 443, можно получить доступ к Windows Admin Center, перейдя по адресу https://\<DNS-имя виртуальной машины\>:\<пользовательский порт\>

При попытке доступа к Windows Admin Center, браузер предложит ввести учетные данные для доступа к виртуальной машине, на котором установлен Windows Admin Center. Здесь необходимо ввести учетные данные, которые находятся в локальных пользователей или группы локальных администраторов виртуальной машины. 

Чтобы добавить другие виртуальные машины в виртуальной сети, убедитесь, что WinRM выполняется на целевых виртуальных машин, выполнив следующую в PowerShell или командную строку на целевой виртуальной Машине. `winrm quickconfig`

Если вы еще не присоединенных к домену виртуальной Машине Azure, виртуальная машина ведет себя как сервер в рабочей группе, вам потребуется убедитесь, что счет для [с помощью Windows Admin Center в рабочую группу](../support/troubleshooting.md#using-windows-admin-center-in-a-workgroup).