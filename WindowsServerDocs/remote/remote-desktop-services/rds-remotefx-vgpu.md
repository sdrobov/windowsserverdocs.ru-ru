---
title: RDS — установка и конфигурация vGPU RemoteFX
description: Сведения о планировании настройки виртуализации графики vGPU RemoteFX.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: a216b84383e6edb3e0537189af5938eb5d62ce42
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71387275"
---
# <a name="set-up-and-configure-remotefx-vgpu-for-remote-desktop-services"></a>Установка и настройка RemoteFX vGPU для служб удаленных рабочих столов


Функция vGPU для RemoteFX предоставляет общий доступ к физическому графическому адаптеру для нескольких виртуальных машин. Виртуальные машины имеют возможность разгрузки отрисовки графической информации, полученной от процессора выделенного графического адаптера. Это содействует уменьшению нагрузки ЦП и улучшению масштабируемости интенсивных рабочих нагрузок графики, выполняемых в VDI виртуальных машин. 

## <a name="remotefx-vgpu-requirements"></a>Требования к RemoteFX vGPU

Требования к операционной системе: 

- Windows Server 2016 или Windows 10;
- GPU совместимый с DX 11.0 с совместимым драйвером WDDM 1.2; 
- включенная роль узла виртуализации удаленных рабочих столов Windows Server (включает роль Hyper-V); 
- сервер, ЦП которого поддерживает SLAT (преобразование адресов второго уровня). 

Требования к гостевым виртуальным машинам:

- гостевая виртуальная машина под управлением клиента Windows Enterprise (Windows 7 с пакетом обновления 1, Windows 8.1, Windows 10) или Windows Server (Windows Server 2012 R2 или Windows Server 2016). Информацию о дополнительной поддержке ОС, см. в разделе [Поддерживаемые конфигурации для служб удаленных рабочих столов](rds-supported-config.md).

Дополнительные рекомендации для гостевых виртуальных машин:

- функции OpenGL и OpenCL доступны только для Windows 10 или Windows Server 2016;  
- DirectX 11.0 доступен только для Windows 8 или более новые гостевых виртуальных машин; 
- узел сеансов удаленных рабочих столов поддерживается RemoteFX vGPU только если он выполняется в качестве [личного сеанса рабочего стола](rds-personal-session-desktops.md);

не забудьте проверить [Развертывание VDI — поддерживаемые гостевые ОС](rds-supported-config.md#vdi-deployment--supported-guest-oss) для гостевых машин.

## <a name="install-remotefx-vgpu"></a>Установка RemoteFX vGPU

Чтобы установить или настроить RemoteFX на узле Windows Server 2016 и Windows 10, выполните следующие действия.

1. Установка операционной системы.
2. Установите последнюю версию Windows 10 или GPU драйверы для Windows Server 2016 с сайта поставщика графической карты.
3. Установите RemoteFX vGPU на узле Windows 10 или Windows Server 2016.
   1. На панели управления узла Windows 10 включите функцию Hyper-V (перейдите к "Панель управления/Программы и компоненты/Включение или отключение компонентов Windows").

      ![Откройте окно компонентов Windows, чтобы включить функцию Hyper-V.](media/rds-hyperv-settings.png)

   2. Установите роль узла виртуализации удаленных рабочих столов (RDVH) на узле Windows Server 2016.
   

4. Теперь создайте и настройте гостевую виртуальную машину.
   1. Создайте виртуальную машину с помощью Windows 10 Корпоративная или Windows Server 2016.
   2. Добавьте трехмерный графический адаптер RemoteFX. Дополнительные сведения о том, как выполнить это действие с помощью командлетов PowerShell или диспетчера Hyper-V, см. в разделе [Настройка трехмерного адаптера для vGPU RemoteFX](#configure-the-remotefx-vgpu-3d-adapter). 

Если в наличии имеется больше одного графического процессора, RemoteFX vGPU будет использовать их все. Однако в некоторых случаях может потребоваться ограничить число графических процессоров, используемых для RemoteFX. Вы можете управлять этим в среде Hyper-V, специально указав, какие графические процессоры *не нужно* использовать для RemoteFX. Выполните следующие шаги. 

   1. В диспетчере Hyper-V перейдите к параметрам Hyper-V.
   2. Щелкните **Физические графические процессоры** в параметрах Hyper-V.
   3. Выберите графический процессор, который не нужно использовать, а затем снимите флажок **Использовать этот графический процессор в RemoteFX**.


### <a name="configure-the-remotefx-vgpu-3d-adapter"></a>Настройка трехмерного адаптера vGPU RemoteFX
Вы можете использовать пользовательский интерфейс диспетчера Hyper-V или командлеты PowerShell, чтобы настроить трехмерный графический адаптер vGPU RemoteFX. 

#### <a name="through-hyper-v-manager"></a>С помощью диспетчера Hyper-V.

1. Убедитесь, что в системе выполнена настройка Hyper-V и виртуальной машины.  
2. Остановите виртуальную машину, если она запущена. 
3. В диспетчере Hyper-V, перейдите к **Параметры виртуальной машины**, а затем нажмите кнопку **Установка оборудования**.
4. Выберите **Трехмерный графический адаптер RemoteFX**и нажмите кнопку **Добавить**. 
5. Задайте максимальное число мониторов, максимальное разрешение монитора и используемой видеопамяти, либо оставьте значения по умолчанию.

   > [!NOTE]
   > - Установка более высоких значений для любой из этих функций окажет влияние на масштабирование, поэтому их следует задавать только при необходимости.
   >
   > - Если вам необходимо использовать 1GB выделенной памяти VRAM, используйте 64-битную гостевую виртуальную машину, вместо 32-битной (x86), чтобы получить лучшие результаты.
6. Нажмите кнопку **ОК**, чтобы завершить настройку.

#### <a name="with-powershell-cmdlets"></a>С помощью командлетов PowerShell.

Выполните следующие командлеты, чтобы добавить, проверить и настроить адаптер: 

```powershell
Add-VMRemoteFx3dVideoAdapter [-CimSession <CimSession[]>] [-ComputerName <String[]>] [-Credential <PSCredential[]>] [-VMName] <String[]> [-Passthru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

Дополнительные сведения см. в разделе [Add-VMRemoteFx3dVideoAdapter](https://technet.microsoft.com/itpro/powershell/windows/hyper-v/add-vmremotefx3dvideoadapter).

```powershell
Get-VMRemoteFx3dVideoAdapter [-CimSession <CimSession[]>] [-ComputerName <String[]>]  [-Credential <PSCredential[]>] [-VMName] <String[]> [<CommonParameters>]
```

Дополнительные сведения см. в разделе [Get-VMRemoteFx3dVideoAdapter](https://technet.microsoft.com/itpro/powershell/windows/hyper-v/get-vmremotefx3dvideoadapter).

```powershell
Set-VMRemoteFx3dVideoAdapter [-CimSession <CimSession[]>] [-ComputerName <String[]>] [-Credential <PSCredential[]>] [-VMName] <String[]> [[-MonitorCount] <Byte>] [[-MaximumResolution] <String>] [[-VRAMSizeBytes] <UInt64>] [-Passthru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

Дополнительные сведения см. в разделе [Set-VMRemoteFx3dVideoAdapter](https://technet.microsoft.com/itpro/powershell/windows/hyper-v/set-vmremotefx3dvideoadapter).

Выполните следующий командлет, чтобы проверить физические графические процессоры:

```powershell
Get-VMRemoteFXPhysicalVideoAdapter [-ComputerName <String[]>] [-Credential <PSCredential[]>] [[-Name] <String[]>] [<CommonParameters>]  
```

Дополнительные сведения см.в разделе [Get-VMRemoteFXPhysicalVideoAdapter](https://technet.microsoft.com/itpro/powershell/windows/hyper-v/get-vmremotefxphysicalvideoadapter).

## <a name="monitor-performance"></a>Производительность монитора

Производительность и масштабирование системы VDI определяются с помощью различных факторов, таких как общий объем памяти графического процессора, объем системной памяти и быстродействие памяти, число ядер и тактовая частота ЦП, скорость хранилища и реализация NUMA.

Поддержка удаленного vGPU в RDS включает в себя следующие счетчики производительности, которые можно просмотреть в системном мониторе (perfmon.exe), чтобы собрать сведения о пропускной способности частоты кадров.

- Графики RemoteFX являются счетчиком сжатия графики протокола удаленного рабочего стола. Например, если вы хотите просмотреть количество кадров, представляемых протоколу удаленного рабочего стола для сжатия, взгляните на счетчик **Входящих кадров в секунду**.
- Сеть RemoteFX является счетчиком для сетевого трафика протокола удаленного рабочего стола. Например **Время кругового пути (RTT)** .
- Управление корневым графическим процессором RemoteFX выполняет измерение доступной и зарезервированной видеопамяти.
- Программное обеспечение RemoteFX предоставляет счетчики для частоты захвата, время отклика графического процессора и других функций.

Чтобы выполнить проверку производительности более низкого уровня, в особенности для устранения неполадок, можно использовать следующие дополнительные счетчики производительности:

- Устройство RemoteFX Synth3D VSC VM 
- Канал транспорта RemoteFX Synth3D VSC VM 
- VSP RemoteFX Synth3D 
- Устройство виртуальной машины RemoteFX Synth3D VSP 
- Канал транспорта виртуальной машины RemoteFX Synth3D VSP
