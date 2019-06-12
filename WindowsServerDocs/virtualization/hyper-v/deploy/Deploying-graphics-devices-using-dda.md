---
title: Развертывание графических устройств, с помощью дискретных назначение устройств
description: Узнайте, как развертывание с помощью DDA графических устройств в Windows Server
ms.prod: windows-server-threshold
ms.service: na
ms.technology: hyper-v
ms.tgt_pltfrm: na
ms.topic: article
author: chrishuybregts
ms.author: chrihu
ms.assetid: 67a01889-fa36-4bc6-841d-363d76df6a66
ms.openlocfilehash: 6c528535fd34f57957a37992843933d4cd9f8824
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66447870"
---
# <a name="deploy-graphics-devices-using-discrete-device-assignment"></a>Развертывание графических устройств, с помощью дискретных назначение устройств

>Область применения. Microsoft Hyper-V Server 2016, Windows Server 2016, Windows Server 2019 г., Microsoft Hyper-V Server 2019 г.  

Начиная с Windows Server 2016, можно использовать назначение отдельных устройств или DDA, для передачи всего устройств PCIe в виртуальную Машину.  Это обеспечит высокий уровень производительности доступ для устройств, таких как [NVMe хранения](./Deploying-storage-devices-using-dda.md) или графических карт из виртуальной Машине, не могут использовать собственные драйверы устройств.  Посетите [спланировать развертывание устройств, с помощью дискретных назначение устройств](../plan/Plan-for-Deploying-Devices-using-Discrete-Device-Assignment.md) узнать больше о каких рабочих устройств, Каковы последствия для безопасности и т. д.

Существует три этапа с помощью устройства с помощью дискретных назначение устройств:
-   Настройка виртуальной Машины для дискретное назначение устройств
-   Отключите устройство от раздела узла
-   Назначение устройства на гостевой виртуальной Машине

Все команда может выполняться на узле на консоли Windows PowerShell с правами администратора.

## <a name="configure-the-vm-for-dda"></a>Настройка виртуальной Машины для DDA
Дискретные назначение устройств накладывает некоторые ограничения на виртуальные машины и следующем шаге необходимо принять меры.

1.  Настройка автоматической остановки Action — виртуальной машины для отключения, выполнив

```
Set-VM -Name VMName -AutomaticStopAction TurnOff
```

### <a name="some-additional-vm-preparation-is-required-for-graphics-devices"></a>Для графических устройств необходима некоторая подготовка дополнительной виртуальной Машины

Некоторое оборудование работает быстрее, если настроить виртуальную Машину в определенным образом.  Дополнительные сведения о ли требуются следующие конфигурации оборудования обратитесь к поставщику оборудования. Дополнительные сведения можно найти на [спланировать развертывание устройств, с помощью дискретных назначение устройств](../plan/Plan-for-Deploying-Devices-using-Discrete-Device-Assignment.md) и об этом [записи блога.](https://blogs.technet.microsoft.com/virtualization/2015/11/23/discrete-device-assignment-gpus/)

1. Включить совмещение записи на ЦП
   ```
   Set-VM -GuestControlledCacheTypes $true -VMName VMName
   ```
2. Настройте пространство MMIO 32-разрядная версия
   ```
   Set-VM -LowMemoryMappedIoSpace 3Gb -VMName VMName
   ```
3. Настроить больше пространства MMIO 32-разрядная версия
   ```
   Set-VM -HighMemoryMappedIoSpace 33280Mb -VMName VMName
   ```
   Обратите внимание, что указанные выше значения пространство MMIO, разумного значения, задаваемые для экспериментов с одного графического Процессора.  Если после запуска виртуальной Машины, устройство содержит сообщение об ошибке не хватает ресурсов, вы скорее всего, потребуется изменить эти значения.  Кроме того Если назначение нескольких GPU, необходимо увеличить эти значения также.

## <a name="dismount-the-device-from-the-host-partition"></a>Отключите устройство от раздела узла
### <a name="optional---install-the-partitioning-driver"></a>Необязательно: установите драйвер секционирования
Дискретные назначение устройства предоставляют изготовители оборудования возможность предоставлять драйвер устранение рисков безопасности со своими устройствами.  Обратите внимание на то, что этот драйвер не так же, как драйвер устройства, который будет установлен на гостевой виртуальной Машине.  Он имеет усмотрение поставщика оборудования для предоставления этого драйвера, тем не менее, если они предоставляют, установите его предварительного к отключении устройства из раздела узла.  Обратитесь к поставщику оборудования узнать больше о при наличии драйвера по устранению рисков
> Если драйвер не секционирование, во время операции отключения необходимо использовать `-force` обходить предупреждение системы безопасности. Прочитайте сведения об аспектах безопасности, это можно сделать на [спланировать развертывание устройств, с помощью дискретных назначение устройств](../plan/Plan-for-Deploying-Devices-using-Discrete-Device-Assignment.md).

### <a name="locating-the-devices-location-path"></a>Поиск путь расположения устройства
Путь к расположению PCI необходим для отключения и подключения устройства из узла.  Путь расположения выглядит следующим образом: `"PCIROOT(20)#PCI(0300)#PCI(0000)#PCI(0800)#PCI(0000)"`.  Дополнительные сведения о найти путь к таблице можно найти здесь: [Планирование развертывания устройств, с помощью дискретных назначение устройств](../plan/Plan-for-Deploying-Devices-using-Discrete-Device-Assignment.md).

### <a name="disable-the-device"></a>Отключить устройство
С помощью диспетчера устройств или PowerShell, убедитесь, устройство «отключить».  

### <a name="dismount-the-device"></a>Отключение устройства
В зависимости от поставщика, если драйвер по устранению рисков, либо необходимо использовать «-force» параметр или нет.
- Если был установлен драйвер по устранению рисков
  ```
  Dismount-VMHostAssignableDevice -LocationPath $locationPath
  ```
- Если при установке драйвера по устранению рисков
  ```
  Dismount-VMHostAssignableDevice -force -LocationPath $locationPath
  ```

## <a name="assigning-the-device-to-the-guest-vm"></a>Назначение устройства на гостевой виртуальной Машине
Последним шагом является сообщить Hyper-V, что у виртуальной Машины должен быть доступ к устройству.  В дополнение к путь, определенный выше необходимо знать имя виртуальной машины.

```
Add-VMAssignableDevice -LocationPath $locationPath -VMName VMName
```

## <a name="whats-next"></a>Что дальше
После успешного подключения устройства на виртуальной машине, теперь можно запустить эту виртуальную Машину и взаимодействовать с устройством, как обычно при запуске на компьютеры без ОС.  Это означает, что теперь вы можете установить драйверы поставщика оборудования на виртуальной машине и приложения будут иметь возможность см. в статье присутствует оборудования.  Это можно проверить, открыв диспетчер устройств в гостевой виртуальной Машине и видеть, что оборудование теперь отображается.

## <a name="removing-a-device-and-returning-it-to-the-host"></a>Удаление устройства и их возвращение в узле
Если вы хотите вернуть он устройство обратно в исходное состояние, необходимо остановить виртуальную Машину и выполните следующее:
```
#Remove the device from the VM
Remove-VMAssignableDevice -LocationPath $locationPath -VMName VMName
#Mount the device back in the host
Mount-VMHostAssignableDevice -LocationPath $locationPath
```
Затем можно снова включить устройство в диспетчере устройств и операционной системы будут иметь возможность взаимодействовать с устройством, еще раз.

## <a name="examples"></a>Примеры

### <a name="mounting-a-gpu-to-a-vm"></a>Подключение графического Процессора для виртуальной Машины
В этом примере мы используем PowerShell для настройки виртуальная машина с именем «ddatest1» первый GPU NVIDIA производителем и назначьте его в виртуальную Машину.  
```
#Configure the VM for a Discrete Device Assignment
$vm =   "ddatest1"
#Set automatic stop action to TurnOff
Set-VM -Name $vm -AutomaticStopAction TurnOff
#Enable Write-Combining on the CPU
Set-VM -GuestControlledCacheTypes $true -VMName $vm
#Configure 32 bit MMIO space
Set-VM -LowMemoryMappedIoSpace 3Gb -VMName $vm
#Configure Greater than 32 bit MMIO space
Set-VM -HighMemoryMappedIoSpace 33280Mb -VMName $vm

#Find the Location Path and disable the Device
#Enumerate all PNP Devices on the system
$pnpdevs = Get-PnpDevice -presentOnly
#Select only those devices that are Display devices manufactured by NVIDIA
$gpudevs = $pnpdevs |where-object {$_.Class -like "Display" -and $_.Manufacturer -like "NVIDIA"}
#Select the location path of the first device that's available to be dismounted by the host.
$locationPath = ($gpudevs | Get-PnpDeviceProperty DEVPKEY_Device_LocationPaths).data[0]
#Disable the PNP Device
Disable-PnpDevice  -InstanceId $gpudevs[0].InstanceId

#Dismount the Device from the Host
Dismount-VMHostAssignableDevice -force -LocationPath $locationPath

#Assign the device to the guest VM.
Add-VMAssignableDevice -LocationPath $locationPath -VMName $vm
```
