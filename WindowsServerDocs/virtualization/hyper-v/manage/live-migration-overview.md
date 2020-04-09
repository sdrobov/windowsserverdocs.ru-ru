---
title: Обзор динамической миграции
description: Содержит обзор функций динамической миграции в Windows Server 2016.
ms.prod: windows-server
ms.technology: compute-hyper-v
ms.topic: article
ms.assetid: 5cc875ab-05c4-439e-b27d-6bfc77054660
author: johncslack
ms.author: joslack
ms.date: 06/27/2017
ms.openlocfilehash: 11fd67f5b4b3c9ce6a8aebe7dac4008f38d0f08e
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80815177"
---
# <a name="live-migration-overview"></a>Обзор динамической миграции

Динамическая миграция — это функция Hyper-V в Windows Server.  Это позволяет прозрачно перемещать работающие виртуальные машины с одного узла Hyper-V на другой без наблюдаемого простоя.  Основное преимущество динамической миграции — гибкость; работающие виртуальные машины не привязаны к одному хост-компьютеру.  Это позволяет выполнять такие действия, как сток определенного узла виртуальных машин перед списанием или обновлением.  При связывании с отказоустойчивым кластером Windows динамическая миграция позволяет создавать высокодоступные и отказоустойчивые системы. 

## <a name="related-technologies-and-documentation"></a>Связанные технологии и документация

Динамическая миграция часто используется совместно с несколькими связанными технологиями, такими как отказоустойчивая кластеризация и System Center Virtual Machine Manager.  Если вы используете динамическая миграция с помощью этих технологий, здесь приведены ссылки на последние документы:
* [Отказоустойчивая кластеризация](../../../failover-clustering/failover-clustering-overview.md) (Windows Server 2016) 
* [System Center Virtual Machine Manager](https://docs.microsoft.com/system-center/vmm/) (System Center 2016) 

Если вы используете более старые версии Windows Server или хотите получить подробные сведения о функциях, появившихся в предыдущих версиях Windows Server, здесь приведены указатели на исторические документы: 
* [Динамическая миграция](https://technet.microsoft.com/library/ee815293(v=ws.10).aspx) (Windows Server 2008 R2)  
* [Динамическая миграция](https://technet.microsoft.com/library/hh831435(v=ws.11).aspx) (Windows Server 2012 R2) 
* [Отказоустойчивая кластеризация](https://technet.microsoft.com/library/hh831579(v=ws.11).aspx) (Windows Server 2012 R2)
* [Отказоустойчивая кластеризация](https://technet.microsoft.com/library/ff182338(v=ws.10).aspx) (Windows Server 2008 R2)
* [System Center Virtual Machine Manager](https://technet.microsoft.com/library/gg610610.aspx) (System Center 2012 R2)
* [System Center Virtual Machine Manager](https://technet.microsoft.com/library/cc917964.aspx) (System Center 2008 R2)

## <a name="live-migration-in-windows-server-2016"></a>динамическая миграция в Windows Server 2016

В Windows Server 2016 существует меньше ограничений на развертывание динамической миграции.  Теперь он работает без отказоустойчивой кластеризации.  Другие функциональные возможности остаются без изменений в предыдущих выпусках динамическая миграция.  Дополнительные сведения о настройке и использовании динамической миграции без отказоустойчивой кластеризации: 
* [Настройка узлов для динамической миграции без отказоустойчивой кластеризации](../deploy/set-up-hosts-for-live-migration-without-failover-clustering.md)
* [Использование динамической миграции без отказоустойчивой кластеризации для перемещения виртуальной машины](use-live-migration-without-failover-clustering-to-move-a-virtual-machine.md)