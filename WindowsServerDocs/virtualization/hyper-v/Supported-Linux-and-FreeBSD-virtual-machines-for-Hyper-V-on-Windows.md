---
title: Поддерживаемые Linux и FreeBSD виртуальных машин для Hyper-V в Windows
description: Список служб интеграции Linux и функций, включенных в каждую версию
ms.prod: windows-server-threshold
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 990ff94a-30fb-434b-b4a2-3804a5245ba6
author: shirgall
ms.author: kathydav
ms.date: 10/03/2016
ms.openlocfilehash: 9df495bdc67b06a675fec050fb4c2960337ce8ca
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59832905"
---
# <a name="supported-linux-and-freebsd-virtual-machines-for-hyper-v-on-windows"></a>Поддерживаемые Linux и FreeBSD виртуальных машин для Hyper-V в Windows

>Область применения. Windows Server 2016, Hyper-V Server 2016, Windows Server 2012 R2, Hyper-V Server 2012 R2, Windows Server 2012, Hyper-V Server 2012, Windows Server 2008 R2, Windows 10, Windows 8.1, Windows 8, Windows 7.1, Windows 7

Для виртуальных машин Linux и FreeBSD в Hyper-V поддерживает эмулированные и Hyper-V-конкретных устройств. При работе с эмулированных устройств, должен быть установлен без дополнительного программного обеспечения. Тем не менее эмулированные устройства не обеспечивают высокую производительность и не могут использовать широкие возможности инфраструктуры виртуальных машин управления, предлагает технологию Hyper-V. Чтобы наиболее эффективно использовать все преимущества, предоставляемые Hyper-V, лучше использовать Hyper v, появляющихся устройства для Linux и FreeBSD. Коллекция драйверы, которые необходимы для запуска Hyper-V-конкретных устройств известны как службы интеграции Linux (LIS) или служб интеграции FreeBSD (BIS).

LIS была добавлена в ядро Linux и обновляется для новых выпусков. Однако дистрибутивов Linux, в зависимости от более старых версиях ядер не предоставляют последние улучшения или исправления. Корпорация Майкрософт предоставляет загрузки, содержащий устанавливаемые драйверы LIS для некоторых установках Linux, в зависимости от этих более старых версиях ядер. Так как поставщики распространения версий Linux Integration Services, рекомендуется установить последнюю доступной для загрузки версии LIS, если это применимо, для установки.

Для других дистрибутивов Linux LIS изменения регулярно интегрированы в ядро операционной системы и приложений, не отдельной загрузки или установки не требуется.

Для более старых версий FreeBSD (до версии 10.0) Корпорация Майкрософт предоставляет порты, которые содержат устанавливаемые драйверы BIS и соответствующие управляющие программы для FreeBSD виртуальных машин. Для более поздних выпусках FreeBSD BIS встроен в операционную систему FreeBSD, и отдельной загрузки или установки не требуется, за исключением загрузки KVP портов, необходимое для FreeBSD 10.0.

> [!TIP]
> - Скачайте [Windows Server 2016](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016) из центра оценки.
> - Скачайте [Microsoft Hyper-V Server 2016](https://www.microsoft.com/evalcenter/evaluate-hyper-v-server-2016) из центра оценки.

Это содержимое предназначена для предоставления сведений, что помогает упростить развертывание Linux и FreeBSD на Hyper-V. Подробные сведения включают:

* Дистрибутивы Linux и FreeBSD выпусков, которые требуют загрузки и установки драйверов LIS или BIS.

* Дистрибутивы Linux и FreeBSD выпусков, которые содержат встроенные драйверы LIS или BIS.

* Распространения карт функций, которые указывают возможностях основные дистрибутивы Linux и FreeBSD выпусков.

* Известные проблемы и решения для каждого распространителя или выпуска.

* Описание компонента для каждого компонента LIS или BIS.

**Хотите внести предложение о компонентах и функциях?** Есть кое-что мы можем сделать лучше? Можно использовать [Windows Server User Voice](https://windowsserver.uservoice.com/forums/295062-linux-support) сайта, чтобы предложить новые функции и возможности для Linux и виртуальные машины FreeBSD в Hyper-V и чтобы узнать мнение других пользователей.

## <a name="in-this-section"></a>В этом разделе

* [Поддерживается CentOS и Red Hat Enterprise Linux виртуальных машин в Hyper-V](Supported-CentOS-and-Red-Hat-Enterprise-Linux-virtual-machines-on-Hyper-V.md)

* [Поддерживаемые виртуальные машины Debian на узле Hyper-V](Supported-Debian-virtual-machines-on-Hyper-V.md)

* [Поддерживаемые виртуальные машины Oracle Linux в Hyper-V](Supported-Oracle-Linux-virtual-machines-on-Hyper-V.md)

* [Поддерживаемые виртуальные машины SUSE в Hyper-V](Supported-SUSE-virtual-machines-on-Hyper-V.md)

* [Поддерживаемые виртуальные машины Ubuntu на базе Hyper-V](Supported-Ubuntu-virtual-machines-on-Hyper-V.md)

* [Поддерживаемые виртуальные машины FreeBSD в Hyper-V](Supported-FreeBSD-virtual-machines-on-Hyper-V.md)

* [Описаниями для виртуальных машин Linux и FreeBSD на Hyper-V](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md)

* [Рекомендации по использованию Linux на Hyper-V](Best-Practices-for-running-Linux-on-Hyper-V.md)

* [Рекомендации по использованию FreeBSD на Hyper-V](Best-practices-for-running-FreeBSD-on-Hyper-V.md)
