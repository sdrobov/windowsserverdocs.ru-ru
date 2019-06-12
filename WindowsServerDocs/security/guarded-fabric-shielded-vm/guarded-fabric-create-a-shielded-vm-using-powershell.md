---
title: Создание экранированной виртуальной Машины с помощью PowerShell
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 0086edb7781a604cc90b9e76d34e5a3dc2725547
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66447523"
---
# <a name="create-a-shielded-vm-using-powershell"></a>Создание экранированной виртуальной Машины с помощью PowerShell

>Относится к: Windows Server 2019 г., Windows Server (полугодовой канал), Windows Server 2016

В рабочей среде обычно используется диспетчер структуры (например VMM) для развертывания экранированных виртуальных машин. Тем не менее см. ниже инструкциям для развертывания и проверить весь сценарий без диспетчера fabric.

По сути вы создадите диск шаблона, файл данных экранирования, файл ответов автоматической установки и другие артефакты безопасности на любом компьютере, а затем скопировать эти файлы на защищенный компьютер и подготовить экранированной виртуальной Машины.

## <a name="create-a-signed-template-disk"></a>Создание диска подписанного шаблона

Чтобы создать новый экранированной виртуальной Машины, необходимо сначала экранированного диска шаблона виртуальной Машины, которое зашифровано с помощью его ОС тома (или boot и корневой секций в Linux) автоматический.
Используйте ссылки ниже дополнительные сведения о том, как создать диск шаблона.

- [Подготовьте диск шаблона Windows](guarded-fabric-create-a-shielded-vm-template.md)
- [Подготовьте диск шаблона Linux](guarded-fabric-create-a-linux-shielded-vm-template.md)

Необходимо также копию каталог подписи тома диска, чтобы создать файл данных экранирования.
Чтобы сохранить этот файл, выполните следующую команду на компьютере, где был создан диск шаблона:

```powershell
Save-VolumeSignatureCatalog -TemplateDiskPath "C:\temp\MyTemplateDisk.vhdx" -VolumeSignatureCatalogPath "C:\temp\MyTemplateDiskCatalog.vsc"
```

## <a name="download-guardian-metadata"></a>Загрузить опекуна метаданных

Для каждой из структур виртуализации, которую вы хотите запустить на экранированной виртуальной Машины необходимо будет получить метаданные для структуры HGS кластеров.
Ваш поставщик услуг размещения, следует предоставить эти сведения.

Если вы находитесь в среде предприятия и может взаимодействовать с сервером HGS, метаданные находится в *http://\<HGSCLUSTERNAME\>/KeyProtection/service/metadata/2014-07/metadata.xml*

## <a name="create-shielding-data-pdk-file"></a>Создайте файл данных экранирования (PDK)

Данные экранирования создается и принадлежит Владельцы виртуальных Машин клиента и содержит секретные данные, необходимые для создания экранированных виртуальных машин, которые должны быть защищены от администратору структуры, такие как пароль администратора экранированной виртуальной Машины.
Данные экранирования шифруется таким образом, чтобы только серверами HGS и клиент может расшифровать его.
После создания владельцем клиента и виртуальных Машин, полученный PDK-файл необходимо скопировать для защищенной структуры.
Дополнительные сведения см. в разделе [что данных экранирования и зачем это необходимые?](guarded-fabric-and-shielded-vms.md#what-is-shielding-data-and-why-is-it-necessary).

Кроме того, вам потребуется файл ответов автоматической установки (unattend.xml для Windows, зависит от для Linux). См. в разделе [создайте файл ответов](guarded-fabric-tenant-creates-shielding-data.md#create-an-answer-file) рекомендации о том, что для включения в файле ответов.

Выполните следующие командлеты на компьютере с помощью средств удаленного администрирования сервера для экранированных виртуальных машин установлен.
Если вы создаете PDK для виртуальной Машины Linux, необходимо выполнить это на сервере под управлением Windows Server версии 1709 или более поздней версии.

 
```powershell
# Create owner certificate, don't lose this!
# The certificate is stored at Cert:\LocalMachine\Shielded VM Local Certificates
$Owner = New-HgsGuardian –Name 'Owner' –GenerateCertificates
 
# Import the HGS guardian for each fabric you want to run your shielded VM
$Guardian = Import-HgsGuardian -Path C:\HGSGuardian.xml -Name 'TestFabric'
 
# Create the PDK file
# The "Policy" parameter describes whether the admin can see the VM's console or not
# Use "EncryptionSupported" if you are testing out shielded VMs and want to debug any issues during the specialization process
New-ShieldingDataFile -ShieldingDataFilePath 'C:\temp\Contoso.pdk' -Owner $Owner –Guardian $guardian –VolumeIDQualifier (New-VolumeIDQualifier -VolumeSignatureCatalogFilePath 'C:\temp\MyTemplateDiskCatalog.vsc' -VersionRule Equals) -WindowsUnattendFile 'C:\unattend.xml' -Policy Shielded
```
    
## <a name="provision-shielded-vm-on-a-guarded-host"></a>Подготовка экранированных виртуальных Машин на защищенном компьютере
Скопируйте файл диска шаблона (ServerOS.vhdx) и PDK-файл (contoso.pdk) на защищенный узел, чтобы подготовить для развертывания.

На защищенный узел установите защищенных Fabric средства модуль PowerShell, который содержит командлет New-ShieldedVM, чтобы упростить процесс подготовки. Если ваш защищенный узел имеет доступ к Интернету, выполните следующую команду:

```powershell
Install-Module GuardedFabricTools -Repository PSGallery -MinimumVersion 1.0.0
```

Вы также можете скачать модуль на другом компьютере с доступом в Интернет и скопировать результирующий `C:\Program Files\WindowsPowerShell\Modules` на защищенный узел.

```powershell
Save-Module GuardedFabricTools -Repository PSGallery -MinimumVersion 1.0.0 -Path C:\temp\
```

После установки модуля, вы будете готовы для подготовки вашей экранированной виртуальной Машины.

```powershell
New-ShieldedVM -Name 'MyShieldedVM' -TemplateDiskPath 'C:\temp\MyTemplateDisk.vhdx' -ShieldingDataFilePath 'C:\temp\Contoso.pdk' -Wait
```

Если ваш диск шаблона содержит ОС на основе Linux, включите `-Linux` флаг при выполнении команды:

```powershell
New-ShieldedVM -Name 'MyLinuxVM' -TemplateDiskPath 'C:\temp\MyTemplateDisk.vhdx' -ShieldingDataFilePath 'C:\temp\Contoso.pdk' -Wait -Linux
```

Проверить содержимого справки с помощью `Get-Help New-ShieldedVM -Full` Дополнительные сведения о других вариантах, можно передать в командлет.

После завершения подготовки виртуальной Машины она вводит фазы специализации определенных Операционных систем, после чего он будет готов для использования.
Убедитесь в том, что для подключения к сети виртуальной Машины, поэтому к нему можно подключиться после его запуска (с помощью протокола удаленного рабочего СТОЛА, PowerShell, SSH или желаемого инструмента управления).

## <a name="running-shielded-vms-on-a-hyper-v-cluster"></a>Запуск экранированных виртуальных машин в кластере Hyper-V

Если вы пытаетесь развернуть экранированные виртуальные машины на кластеризованный защищенных узлов (с помощью отказоустойчивый кластер Windows), можно настроить экранированной виртуальной Машины, чтобы обеспечивать высокую доступность с помощью следующего командлета:

```powershell
Add-ClusterVirtualMachineRole -VMName 'MyShieldedVM' -Cluster <Hyper-V cluster name>
```

Экранированная виртуальная машина может теперь выполнить динамическую миграцию в кластере.

## <a name="next-step"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Развертывание экранированных с помощью VMM](guarded-fabric-tenant-deploys-shielded-vm-using-vmm.md)