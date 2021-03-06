---
title: Планирование ускорения GPU в Windows Server
description: Узнайте о различных технологиях Hyper-V для ускорения GPU, включая ДДА и RemoteFX.
ms.prod: windows-server
ms.reviewer: rickman
author: rick-man
ms.author: rickman
manager: stevelee
ms.topic: article
ms.date: 07/14/2020
ms.openlocfilehash: 0177ce6346741998a0a9f97817e3811561bb02fb
ms.sourcegitcommit: acfdb7b2ad283d74f526972b47c371de903d2a3d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2020
ms.locfileid: "87768824"
---
# <a name="plan-for-gpu-acceleration-in-windows-server"></a>Планирование ускорения GPU в Windows Server

> Область применения: Windows Server 2016, Microsoft Hyper-V Server 2016, Windows Server 2019, Microsoft Hyper-V Server 2019

В этой статье описываются возможности виртуализации графики, доступные в Windows Server.

## <a name="when-to-use-gpu-acceleration"></a>Когда следует использовать ускорение GPU

В зависимости от рабочей нагрузки может потребоваться ускорение GPU. Прежде чем выбрать ускорение GPU, необходимо принять во внимание следующее.

- **Рабочие нагрузки для удаленного взаимодействия между приложениями и настольными системами (VDI/DaAS)**. Если вы создаете приложение или настольную службу удаленного взаимодействия с Windows Server, рассмотрите Каталог приложений, которые предполагается запускать пользователям. Некоторые типы приложений, такие как приложения САПР и камера, приложения моделирования, игры и приложения отрисовки и визуализации, полагаются на трехмерную отрисовку, чтобы обеспечить гладкое и быстро реагирующее взаимодействие. Большинство клиентов считают, что GPU имеет смысл для разумного взаимодействия с пользователями этих типов приложений.
- **Удаленная визуализация, кодирование и визуализация рабочие нагрузки**. Эти графические рабочие нагрузки обычно зависят от специализированных возможностей GPU, таких как эффективная трехмерная отрисовка и кодирование и декодирование кадров, для достижения целей экономичности и пропускной способности. Для такого рода рабочих нагрузок одна виртуальная машина с поддержкой GPU может соответствовать пропускной способности многих виртуальных машин, использующих только ЦП.
- **Рабочие нагрузки HPC и ML**. для вычислительных рабочих нагрузок с высокой производительностью, например для высокопроизводительных вычислительных операций и обучения моделей машинного обучения или вывода, графические процессоры могут значительно сократить время, чтобы получить результат, время на вывод и время обучения. Кроме того, они могут обеспечить лучшую экономичность, чем архитектура только с ЦП на сравнимом уровне производительности. Многие платформы HPC и машинного обучения имеют возможность включить ускорение GPU; Определите, может ли это помочь вам в конкретной рабочей нагрузке.

## <a name="gpu-virtualization-in-windows-server"></a>Виртуализация GPU в Windows Server

Технологии виртуализации GPU позволяют выполнять ускорение GPU в виртуализованной среде, обычно в виртуальных машинах. Если Рабочая нагрузка виртуализована с помощью Hyper-V, необходимо использовать виртуализацию графики, чтобы обеспечить ускорение GPU от физического GPU до виртуализированных приложений или служб. Однако если Рабочая нагрузка выполняется непосредственно на физических узлах Windows Server, то нет необходимости в виртуализации графики. у ваших приложений и служб уже есть доступ к возможностям GPU и интерфейсам API, которые изначально поддерживаются в Windows Server.

Для виртуальных машин Hyper-V в Windows Server доступны следующие технологии графической виртуализации:

- [Дискретное назначение устройств (ДДА)](#discrete-device-assignment-dda)
- [RemoteFX vGPU](#remotefx-vgpu)

Помимо рабочих нагрузок виртуальных машин, Windows Server также поддерживает ускорение GPU контейнерных рабочих нагрузок в контейнерах Windows. Дополнительные сведения см. [в разделе ускорение GPU в контейнерах Windows](https://docs.microsoft.com/virtualization/windowscontainers/deploy-containers/gpu-acceleration).

## <a name="discrete-device-assignment-dda"></a>Дискретное назначение устройств (ДДА)

Дискретное назначение устройств (ДДА), также называемое сквозным ПРОЦЕССОРом, позволяет выделить один или несколько физических GPU для виртуальной машины. В развертывании ДДА виртуализированные рабочие нагрузки работают на собственном драйвере и, как правило, имеют полный доступ к функциональным возможностям GPU. ДДА обеспечивает наивысший уровень совместимости приложений и потенциальной производительности. ДДА также может обеспечить ускорение GPU для виртуальных машин Linux в соответствии с поддержкой.

Развертывание ДДА может ускорить только ограниченное число виртуальных машин, так как каждый физический GPU может обеспечить ускорение до одной виртуальной машины. Если вы разрабатываете службу, архитектура которой поддерживает общие виртуальные машины, рассмотрите возможность размещения нескольких ускоренных рабочих нагрузок на каждой виртуальной машине. Например, если вы создаете службу удаленного взаимодействия для настольных компьютеров с RDS, вы можете улучшить масштабирование пользователей, используя многосеансовые возможности Windows Server для размещения нескольких пользовательских настольных систем на каждой виртуальной машине. Эти пользователи будут использовать преимущества ускорения GPU.

Дополнительные сведения см. в следующих статьях:

- [Планирование развертывания дискретного назначения устройств](plan-for-deploying-devices-using-discrete-device-assignment.md)
- [Развертывание графических устройств с помощью дискретного назначения устройств](../deploy/Deploying-graphics-devices-using-dda.md)

## <a name="remotefx-vgpu"></a>RemoteFX vGPU

> [!NOTE]
> Из соображений безопасности процессор RemoteFX vGPU по умолчанию отключен для всех версий Windows, начиная с обновления для системы безопасности за 14 июля 2020 г. См. [KB 4570006](https://support.microsoft.com/help/4570006).

Виртуальный графический процессор RemoteFX — это технология виртуализации графики, которая позволяет совместно использовать один физический GPU на нескольких виртуальных машинах. В развертывании RemoteFX виртуализованные рабочие нагрузки выполняются на 3D-адаптере RemoteFX корпорации Майкрософт, который координирует запросы обработки GPU между узлом и гостями. Виртуальная среда RemoteFX наиболее подходит для рабочей роли и высокопроизводительных рабочих нагрузок, когда выделенные ресурсы GPU не требуются. Виртуальный графический процессор RemoteFX может предоставлять только ускорение GPU для виртуальных машин Windows.

Дополнительные сведения см. в следующих статьях:

- [Развертывание графических устройств с помощью vGPU RemoteFX](../deploy/deploy-graphics-devices-using-remotefx-vgpu.md)
- [Поддержка 3D-видеоадаптера RemoteFX (vGPU)](../../../remote/remote-desktop-services/rds-supported-config.md#remotefx-3d-video-adapter-vgpu-support)

## <a name="comparing-dda-and-remotefx-vgpu"></a>Сравнение ДДА и виртуальных GPU RemoteFX

При планировании развертывания необходимо учитывать следующие функциональные возможности и поддержку различий между технологиями виртуализации графики.

| Описание: | RemoteFX vGPU | Дискретное назначение устройств |
|--|--|--|
| Модель ресурсов GPU | Выделенный или общий | Только выделенные |
| Плотность виртуальных машин | Высокий (один или несколько графических процессоров для нескольких виртуальных машин) | Низкий (один или несколько GPU на одной виртуальной машине) |
| Совместимость приложений | DX 11.1, OpenGL 4.4, OpenCL 1.1 | Все возможности графического процессора, предоставляемое поставщиком (12 DX, OpenGL, CUDA). |
| AVC444 | По умолчанию включено | Доступно через групповая политика |
| Видеопамять графического процессора. | До 1 ГБ выделенной видеопамяти | К видеопамяти, поддерживаемой графическим процессором. |
| Частота кадров | До 30 кадров в секунду. | До 60 кадров в секунду. |
| Драйвер графического процессора в гостевом режиме. | Драйвер 3D-видеоадаптера RemoteFX (Майкрософт) | Драйвер поставщика GPU (NVIDIA, AMD, Intel) |
| Поддержка ОС узла | Windows Server 2016 | Windows Server 2016; Windows Server 2019 |
| Поддержка гостевых операционных систем | Windows Server 2012 R2; Windows Server 2016; Windows 7 SP1; Windows 8.1; Windows 10 | Windows Server 2012 R2; Windows Server 2016; Windows Server 2019; Windows 10; Linux |
| Низкоуровневая оболочка | Microsoft Hyper-V | Microsoft Hyper-V |
| Оборудование графического процессора | Графические процессоры корпоративного класса (например, Nvidia Quadro/GRID или AMD FirePro) | Графические процессоры корпоративного класса (например, Nvidia Quadro/GRID или AMD FirePro) |
| Настройка серверного оборудования. | Никаких особых требований | Современный сервер предоставляет IOMMU для операционной системы (обычно соответствующее оборудование SR-IOV) |
