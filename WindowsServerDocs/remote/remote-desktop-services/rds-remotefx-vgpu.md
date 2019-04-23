---
title: RDS - Установка и настройка vGPU RemoteFX
description: Сведения о планировании для настройки виртуализации графики vGPU RemoteFX.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: remote-desktop-services
ms.author: elizapo
ms.date: 03/23/2017
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0263fa6b-2185-4cc3-99ef-3588e2f4ada5
author: lizap
manager: scottman
ms.openlocfilehash: 3e7da1a70826dc720a96ceb3fe5d04868943f163
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59876845"
---
# <a name="set-up-and-configure-remotefx-vgpu-for-remote-desktop-services"></a>Установка и настройка RemoteFX vGPU для служб удаленных рабочих столов


Функция vGPU RemoteFX позволяет нескольким виртуальным машинам общий доступ к адаптеру физической графики. Виртуальные машины имеют возможность разгрузки отрисовка графики, полученные от обработчика для выделенных графического адаптера. Это будет уменьшить нагрузку на ЦП и улучшить масштабируемость для графических интенсивных рабочих нагрузок, выполняемых на виртуальных машинах VDI. 

## <a name="remotefx-vgpu-requirements"></a>Требования к vGPU RemoteFX

Требования к системе: 

- Windows Server 2016 или Windows 10
- DX 11.0 совместимым графическим Процессором с совместимый драйвер WDDM 1.2 
- Включенной роли узла виртуализации удаленных рабочих Столов Windows Server (включает роль Hyper-V) 
- Сервер, ЦП которого поддерживает SLAT (трансляция адресов второго уровня) 

Требования к гостевой виртуальной Машины.

- Гостевой виртуальной Машины под управлением Windows Enterprise client (Windows 7 с пакетом обновления 1, Windows 8.1, Windows 10) или Windows Server (Windows Server 2012 R2 или Windows Server 2016). Для дополнительных OS поддерживают, приведен здесь [поддерживаемые конфигурации для служб удаленных рабочих столов](rds-supported-config.md).

Дополнительные рекомендации для гостевых виртуальных машин:

- OpenGL и OpenCL функция доступна только в Windows 10 или Windows Server 2016.  
- DirectX 11.0 доступен только в Windows 8 или более новые гостевых виртуальных машин. 
- Узел сеансов удаленных рабочих столов поддерживается только с RemoteFX vGPU если он выполняется как [desktop личных сеансов](rds-personal-session-desktops.md).

Для гостевых виртуальных МАШИН, не забудьте проверить [развертывание VDI - поддерживаемы гостевых ОС](rds-supported-config.md#vdi-deployment--supported-guest-oss).

## <a name="install-remotefx-vgpu"></a>Установка RemoteFX vGPU

Установка и настройка RemoteFX на узле Windows Server 2016 и Windows 10, следуйте инструкциям ниже:

1. Установка операционной системы.
2. Установите последнюю Windows 10 и Windows Server 2016 GPU драйверов с сайта поставщика графической карты.
3. Установите RemoteFX vGPU на узле Windows 10 и Windows Server 2016:
   1. На узле Windows 10 включите функцию Hyper-V на панели управления (перейдите к шагу программ панели управления и компонентов или включение компонентов Windows или отключить):

      ![Окно компоненты Windows, чтобы включить компонент Hyper-V](media/rds-hyperv-settings.png)

   2. На узле Windows Server 2016 установите роль узла виртуализации удаленных рабочих столов (RDVH).
   

4. Теперь создайте и настройте гостевой виртуальной Машине.
   1. Создание виртуальной Машины с Windows 10 Корпоративная или Windows Server 2016.
   2. Добавьте адаптер RemoteFX 3D-графики. См. в разделе [Настройка трехмерным адаптером vGPU RemoteFX](#configure-the-remotefx-vgpu-3d-adapter) сведения о том, как сделать это с помощью командлетов PowerShell или диспетчера Hyper-V. 

RemoteFX vGPU будет использовать все графические процессоры, когда доступны несколько. Однако в некоторых случаях может потребоваться ограничить какие процессоры используются RemoteFX. В среде Hyper-V, можно управлять, специально указав, какие следует GPU *не* использоваться RemoteFX. Выполните следующие шаги. 

   1. Перейдите к параметрам Hyper-V в диспетчере Hyper-V.
   2. Нажмите кнопку **физические процессоры** в параметры Hyper-V.
   3. Выберите, графического Процессора, вы не хотите использовать, а затем снимите **использовать этот GPU с RemoteFX**.


### <a name="configure-the-remotefx-vgpu-3d-adapter"></a>Настройте адаптер 3D vGPU RemoteFX
Пользовательский Интерфейс диспетчера Hyper-V или PowerShell командлеты можно использовать для настройки адаптера трехмерной графики vGPU RemoteFX. 

#### <a name="through-hyper-v-manager"></a>В диспетчере Hyper-V:

1. Убедитесь, настройки системы с Hyper-V и настроил виртуальную Машину.  
2. Остановите виртуальную Машину, если она запущена. 
3. В диспетчере Hyper-V, перейдите к **параметры виртуальной Машины**, а затем нажмите кнопку **Установка оборудования**.
4. Выберите **трехмерный видеоадаптер RemoteFX**и нажмите кнопку **добавить**. 
5. Задать максимальное число мониторов, максимальное разрешение монитора и видеопамяти, либо оставьте значения по умолчанию.

   > [!NOTE]
   > - Установка более высокие значения для любого из этих вариантов окажет влияния на масштабирование, поэтому следует задавать только самое необходимое.
   >
   > - При необходимости использовать 1 ГБ выделенной видеопамяти, используйте 64-разрядную гостевую виртуальную Машину вместо 32-(x86) для получения наилучших результатов.
6. Нажмите кнопку **ОК** закончить настройку.

#### <a name="with-powershell-cmdlets"></a>С помощью командлетов PowerShell:

Выполните следующие командлеты, чтобы добавить, просмотреть и настроить адаптер: 

```powershell
Add-VMRemoteFx3dVideoAdapter [-CimSession <CimSession[]>] [-ComputerName <String[]>] [-Credential <PSCredential[]>] [-VMName] <String[]> [-Passthru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

Дополнительные сведения см. [Add-VMRemoteFx3dVideoAdapter](https://technet.microsoft.com/itpro/powershell/windows/hyper-v/add-vmremotefx3dvideoadapter).

```powershell
Get-VMRemoteFx3dVideoAdapter [-CimSession <CimSession[]>] [-ComputerName <String[]>]  [-Credential <PSCredential[]>] [-VMName] <String[]> [<CommonParameters>]
```

Дополнительные сведения см. [Get-VMRemoteFx3dVideoAdapter](https://technet.microsoft.com/itpro/powershell/windows/hyper-v/get-vmremotefx3dvideoadapter)

```powershell
Set-VMRemoteFx3dVideoAdapter [-CimSession <CimSession[]>] [-ComputerName <String[]>] [-Credential <PSCredential[]>] [-VMName] <String[]> [[-MonitorCount] <Byte>] [[-MaximumResolution] <String>] [[-VRAMSizeBytes] <UInt64>] [-Passthru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

Дополнительные сведения см. [Set-VMRemoteFx3dVideoAdapter](https://technet.microsoft.com/itpro/powershell/windows/hyper-v/set-vmremotefx3dvideoadapter).

Выполните следующий командлет, чтобы просмотреть физические процессоры GPU:

```powershell
Get-VMRemoteFXPhysicalVideoAdapter [-ComputerName <String[]>] [-Credential <PSCredential[]>] [[-Name] <String[]>] [<CommonParameters>]  
```

Дополнительные сведения см. [Get-VMRemoteFXPhysicalVideoAdapter](https://technet.microsoft.com/itpro/powershell/windows/hyper-v/get-vmremotefxphysicalvideoadapter).

## <a name="monitor-performance"></a>Мониторинг производительности

Производительность и масштабирование системы VDI определяются различных факторов, таких как общий объем памяти GPU, объем системной памяти и скорости доступа к памяти, число ядер ЦП и тактовой частоты ЦП, скорость хранилища и реализации архитектуры NUMA.

Поддержка удаленного vGPU в RDS включает в себя следующие счетчики производительности, которые можно просмотреть в системный монитор (perfmon.exe) для сбора сведений о пропускной способности частоты кадров.

- Графики RemoteFX - счетчики для сжатия графики протокола удаленного рабочего стола. Например, если вы хотите просмотреть количество кадров, представляемых протоколу удаленного рабочего стола для сжатия, взгляните на **Frames/Second ввода** счетчика.
- RemoteFX сети — счетчики для сетевой трафик протокола удаленного рабочего стола. Например **время кругового пути (RTT)**.
- Управление GPU RemoteFX корневой — измерения VRAM доступна и зарезервированные.
- Программное обеспечение RemoteFX — предоставляет счетчики для скорости регистрации, время отклика GPU и других.

Для более низкого уровня мониторинга производительности, особенно для устранения неполадок, можно использовать следующие счетчики производительности:

- RemoteFX Synth3D виртуальной Машины VSC устройства 
- Канал транспорта RemoteFX Synth3D виртуальной Машины VSC 
- VSP RemoteFX Synth3D 
- RemoteFX Synth3D виртуальной Машины VSP устройства 
- RemoteFX Synth3D виртуальной Машины VSP канала
