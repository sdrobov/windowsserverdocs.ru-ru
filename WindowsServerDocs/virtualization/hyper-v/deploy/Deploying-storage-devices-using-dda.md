---
title: Развертывание NVMe запоминающих устройств, с помощью дискретных назначение устройств
description: Узнайте, как развертывание с помощью DDA запоминающие устройства
ms.prod: windows-server-threshold
ms.service: na
ms.technology: hyper-v
ms.tgt_pltfrm: na
ms.topic: article
author: chrishuybregts
ms.author: chrihu
ms.assetid: 1c36107e-78c9-4ec0-a313-6ed557ac0ffc
ms.openlocfilehash: d6fe54789d37386d5dc782ef8a2ca26b47adc69e
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59841365"
---
# <a name="deploy-nvme-storage-devices-using-discrete-device-assignment"></a>Развертывание NVMe запоминающих устройств, с помощью дискретных назначение устройств

>Область применения. Microsoft Hyper-V Server 2016, Windows Server 2016

Начиная с Windows Server 2016, можно использовать назначение отдельных устройств или DDA, для передачи всего устройств PCIe в виртуальную Машину.  Таким образом высокопроизводительных доступ для устройств, таких как хранилище NVMe или графические платы из на виртуальной машине, не могут использовать собственные драйверы устройств.  Посетите [спланировать развертывание устройств, с помощью дискретных назначение устройств](../plan/Plan-for-Deploying-Devices-using-Discrete-Device-Assignment.md) узнать больше о каких рабочих устройств, Каковы последствия для безопасности и т. д. С помощью устройства с DDA трех этапов:
-   Настройка виртуальной Машины для DDA
-   Отключите устройство от раздела узла
-   Назначение устройства на гостевой виртуальной Машине

Все команда может выполняться на узле на консоли Windows PowerShell с правами администратора.

## <a name="configure-the-vm-for-dda"></a>Настройка виртуальной Машины для DDA
Дискретные назначение устройств накладывает некоторые ограничения на виртуальные машины и следующем шаге необходимо принять меры.

1.  Настройка автоматической остановки Action — виртуальной машины для отключения, выполнив

```
Set-VM -Name VMName -AutomaticStopAction TurnOff
```

## <a name="dismount-the-device-from-the-host-partition"></a>Отключите устройство от раздела узла

### <a name="locating-the-devices-location-path"></a>Поиск путь расположения устройства
Путь к расположению PCI необходим для отключения и подключения устройства из узла.  Путь расположения выглядит следующим образом: `"PCIROOT(20)#PCI(0300)#PCI(0000)#PCI(0800)#PCI(0000)"`.   Дополнительные сведения о найти путь к таблице можно найти здесь: [Планирование развертывания устройств, с помощью дискретных назначение устройств](../plan/Plan-for-Deploying-Devices-using-Discrete-Device-Assignment.md).

### <a name="disable-the-device"></a>Отключить устройство
С помощью диспетчера устройств или PowerShell, убедитесь, устройство «отключить».  

### <a name="dismount-the-device"></a>Отключение устройства
```
Dismount-VMHostAssignableDevice -LocationPath $locationPath
```

## <a name="assigning-the-device-to-the-guest-vm"></a>Назначение устройства на гостевой виртуальной Машине
Последним шагом является сообщить Hyper-V, что у виртуальной Машины должен быть доступ к устройству.  В дополнение к путь, определенный выше необходимо знать имя виртуальной машины.

```
Add-VMAssignableDevice -LocationPath $locationPath -VMName VMName
```

## <a name="whats-next"></a>Что дальше
После успешного подключения устройства на виртуальной машине, теперь можно запустить эту виртуальную Машину и взаимодействовать с устройством, как обычно при запуске на компьютеры без ОС.  Это можно проверить, открыв диспетчер устройств в гостевой виртуальной Машине и видеть, что оборудование теперь отображается.

## <a name="removing-a-device-and-returning-it-to-the-host"></a>Удаление устройства и их возвращение в узле
Если вы хотите вернуть он устройство обратно в исходное состояние, необходимо остановить виртуальную Машину и выполните следующее:
```
#Remove the device from the VM
Remove-VMAssignableDevice -LocationPath $locationPath -VMName VMName
#Mount the device back in the host
Mount-VMHostAssignableDevice -LocationPath $locationPath
```
Затем можно снова включить устройство в диспетчере устройств и операционной системы будут иметь возможность взаимодействовать с устройством, еще раз.
