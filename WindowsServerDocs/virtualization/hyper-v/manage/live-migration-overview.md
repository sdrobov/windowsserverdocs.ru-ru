---
title: Обзор динамической миграции
description: Содержит общие сведения о функции динамической миграции в Windows Server 2016.
ms.prod: windows-server-threshold
ms.service: na
ms.technology: compute-hyper-v
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5cc875ab-05c4-439e-b27d-6bfc77054660
author: johncslack
ms.author: joslack
ms.date: 06/27/2017
ms.openlocfilehash: 2bbe897ffb8b200a72fac5a662e518d4a4be1131
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59887855"
---
# <a name="live-migration-overview"></a>Обзор динамической миграции

Динамическая миграция — это функция Hyper-V в Windows Server.  Он позволяет прозрачное перемещение работающих виртуальных машин с одного узла Hyper-V на другой без установленного времени простоя.  Основным преимуществом динамической миграции является гибкость; работающие виртуальные машины не привязаны к одного хост-компьютера.  Благодаря этому такие действия, как завершение работы определенного узла виртуальных машин перед ее из эксплуатации или ее обновление.  При совместном использовании с отказоустойчивой кластеризацией Windows, динамическая миграция обеспечивает создание высокой доступности и отказоустойчивости системы нечувствительного к ошибкам. 

## <a name="related-technologies-and-documentation"></a>Связанные технологии и документация

Динамическая миграция часто используется в сочетании с нескольких связанных технологий, таких как отказоустойчивая кластеризация и System Center Virtual Machine Manager.  При использовании динамической миграции с помощью этих технологий, ниже приведены ссылки на их последние версии документации.
* [Отказоустойчивая кластеризация](../../../failover-clustering/failover-clustering-overview.md) (Windows Server 2016) 
* [System Center Virtual Machine Manager](https://docs.microsoft.com/system-center/vmm/) (System Center 2016) 

Если вы используете более старых версий Windows Server или нужны сведения о функциях, представленных в предыдущих версиях Windows Server, ниже приведены ссылки на документацию по ведением журнала. 
* [Динамическая миграция](https://technet.microsoft.com/library/ee815293(v=ws.10).aspx) (Windows Server 2008 R2)  
* [Динамическая миграция](https://technet.microsoft.com/library/hh831435(v=ws.11).aspx) (Windows Server 2012 R2) 
* [Отказоустойчивая кластеризация](https://technet.microsoft.com/library/hh831579(v=ws.11).aspx) (Windows Server 2012 R2)
* [Отказоустойчивая кластеризация](https://technet.microsoft.com/library/ff182338(v=ws.10).aspx) (Windows Server 2008 R2)
* [System Center Virtual Machine Manager](https://technet.microsoft.com/library/gg610610.aspx) (System Center 2012 R2)
* [System Center Virtual Machine Manager](https://technet.microsoft.com/library/cc917964.aspx) (System Center 2008 R2)

## <a name="live-migration-in-windows-server-2016"></a>Динамическая миграция в Windows Server 2016

В Windows Server 2016 существует меньше ограничения на развертывание динамической миграции.  Теперь он будет работать без отказоустойчивой кластеризации.  Другие функциональные возможности остаются изменились по сравнению с предыдущими выпусками динамической миграции.  Дополнительные сведения о настройке и использовании динамической миграции без отказоустойчивой кластеризации: 
* [Настройка узлов для динамической миграции без отказоустойчивой кластеризации](../deploy/set-up-hosts-for-live-migration-without-failover-clustering.md)
* [Использование динамической миграции без отказоустойчивой кластеризации для перемещения виртуальной машины](use-live-migration-without-failover-clustering-to-move-a-virtual-machine.md)