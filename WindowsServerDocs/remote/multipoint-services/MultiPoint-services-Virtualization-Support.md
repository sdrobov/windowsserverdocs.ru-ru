---
title: Поддержка виртуализации служб MultiPoint
description: Описывает использование MultiPoint Services с помощью Hyper-V
ms.custom: na
ms.date: 07/22/2016
ms.prod: windows-server-threshold
ms.technology: multipoint-services
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3f0864b8-a087-4890-94ef-05efbd3c4241
author: evaseydl
manager: scottman
ms.author: evas
ms.openlocfilehash: 06d518dcea154ac2bab49a7d0e83a90f96be6e44
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59872525"
---
# <a name="multipoint-services-virtualization-support"></a>Поддержка виртуализации служб MultiPoint
MultiPoint Services поддерживает роль Hyper-V двумя способами:  
  
-   MultiPoint Services можно развернуть в качестве гостевой операционной системы на сервере с Hyper-V.  
  
-   MultiPoint Services может использоваться как сервер виртуализации.   
  
Выполнение MultiPoint Services на виртуальной машине обеспечивает использование средства Hyper-V для управления операционными системами. Эти средства включают функции контрольных точек и отката, и они дают возможность экспорта и импорта виртуальных машин. Для более крупных установок можно консолидировать серверы, выполнив несколько виртуальных компьютеров с MultiPoint Services на одном физическом сервере. Вот возможные сценарии.  
  
-   Одной аудитории или лаборатории имеет более 20 рабочих мест. Вместо того чтобы развертывание нескольких физических компьютерах, на котором работает MultiPoint Services, можно развернуть несколько виртуальных машин на одном физическом компьютере.  
  
    > [!NOTE]  
    > Вы можете управлять несколькими серверами MultiPoint, физического или виртуального с единой консоли MultiPoint Manager.  
  
-   MultiPoint server запущен на виртуальной машине с другой серверной инфраструктуры на одном физическом компьютере. В этом случае эта инфраструктура сервера позволяет централизовать домен, безопасности и данных для сети. MultiPoint server предоставляет службы удаленных рабочих столов и централизует настольных компьютеров.  
  
> [!NOTE]  
> При выполнении MultiPoint Services на виртуальной машине, поддерживаются USB через Ethernet и станций клиента удаленного рабочего СТОЛА. Прямой видео и USB zero клиенту, подключившемуся станций не поддерживаются.  
  
Дополнительные сведения о роли Hyper-V, см. в разделе [Hyper-V](../../virtualization/hyper-v/hyper-v-on-windows-server.md).  