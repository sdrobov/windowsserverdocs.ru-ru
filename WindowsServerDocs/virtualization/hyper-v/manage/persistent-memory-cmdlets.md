---
title: Командлеты для настройки устройств постоянной памяти для виртуальных машин Hyper-V
description: Как настроить устройства постоянной памяти для виртуальных машин Hyper-V
ms.prod: windows-server-threshold
ms.service: na
manager: jasgroce
ms.technology: compute-hyper-v
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b5715c02-a90f-4de9-a71e-0fc08039ba1d
author: coreyp-at-msft
ms.author: coreyp
ms.openlocfilehash: fd1b04ce74f0b8d490529d2a7f65091f5847d0f4
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59878185"
---
# <a name="cmdlets-for-configuring-persistent-memory-devices-for-hyper-v-vms"></a>Командлеты для настройки устройств постоянной памяти для виртуальных машин Hyper-V

>Область применения. Windows Server 2019

В этой статье системных администраторов и ИТ-специалистов предоставляются сведения о настройке виртуальных машин Hyper-V с постоянной памяти (также называемые памяти класса хранилища или NVDIMM). JDEC-совместимые устройства постоянной памяти NVDIMM-N поддерживаются в Windows Server 2016 и Windows 10 и предоставляют доступ на уровне байт на устройствах долговременного очень низкой задержкой. Устройства постоянной памяти виртуальной Машины поддерживаются в Windows Server 2019. 

## <a name="create-a-persistent-memory-device-for-a-vm"></a>Создание постоянной памяти устройства для виртуальной Машины

Используйте **[New-VHD](https://docs.microsoft.com/powershell/module/hyper-v/new-vhd?view=win10-ps)** командлет для создания постоянной памяти устройства для виртуальной Машины. Устройства должны создаваться на существующий том NTFS DAX.  Новое расширение имени файла (.vhdpmem) используется для указания, что устройство является постоянной памяти устройства. Поддерживается только в фиксированный формат VHD.

**Пример:** `New-VHD d:\VMPMEMDevice1.vhdpmem -Fixed -SizeBytes 4GB`

## <a name="create-a-vm-with-a-persistent-memory-controller"></a>Создание виртуальной Машины с контроллером постоянной памяти



Используйте **командлет New-VM** для создания виртуальной Машины поколения 2 заданный объем памяти и путь к vhdx-образ. Затем с помощью **VMPmemController добавить** по добавлению контроллера в постоянной памяти на виртуальную Машину.

**Пример:** 
    
    New-VM -Name "ProductionVM1" -MemoryStartupBytes 1GB -VHDPath c:\vhd\BaseImage.vhdx

    Add-VMPmemController ProductionVM1x

## <a name="attach-a-persistent-memory-device-to-a-vm"></a>Подключение к виртуальной Машине постоянной памяти устройства

Используйте **[Add-VMHardDiskDrive](https://docs.microsoft.com/powershell/module/hyper-v/add-vmharddiskdrive?view=win10-ps)** для присоединения устройства постоянной памяти на виртуальную Машину

**Пример:** `Add-VMHardDiskDrive ProductionVM1 PMEM -ControllerLocation 1 -Path D:\VPMEMDevice1.vhdpmem`

Устройства постоянной памяти на виртуальной машине Hyper-V отображаются в том, как устройство постоянной памяти, потребляемый и под управлением операционной системы. Гостевые операционные системы можно использовать устройство в качестве блока или томе DAX. При постоянной памяти устройства в виртуальной Машине используются как том DAX, они задействуют высокоскоростной уровне байт адрес возможности узла устройства (без виртуализации ввода-вывода, для которого на пути кода). 

>[!NOTE] 
>Постоянной памяти поддерживается только для виртуальных машин Hyper-V поколения 2. Динамической миграции и миграции хранилища не поддерживаются для виртуальных машин с постоянной памяти. Рабочие контрольные точки виртуальных машин не содержат состояние постоянной памяти. 