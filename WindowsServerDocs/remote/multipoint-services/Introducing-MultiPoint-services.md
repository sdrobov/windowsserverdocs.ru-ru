---
title: Основные сведения о службах MultiPoint
description: Содержит общие сведения о службах MultiPoint, способах предоставления общего доступа к системе нескольким пользователям.
ms.custom: na
ms.date: 07/22/2016
ms.prod: windows-server
ms.technology: multipoint-services
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1cbef744-4661-4ba9-9e2b-0bbd8854fd5c
author: evaseydl
manager: scottman
ms.author: evas
ms.openlocfilehash: a0497f9dfd39648a94d9fb832f4404491955c06a
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71395353"
---
# <a name="introducing-multipoint-services"></a>Основные сведения о службах MultiPoint
Роль служб MultiPoint в Windows Server 2016 позволяет нескольким пользователям с собственными независимыми и привычными возможностями Windows совместно использовать один компьютер. Существует несколько способов доступа пользователей к своим сеансам. Один из способов — удаленное взаимодействие с сервером с помощью [приложений удаленного рабочего стола](../remote-desktop-services/clients/remote-desktop-clients.md) с любым устройством. Другой способ — благодаря физическим станциям, подключенным к серверу MultiPoint:  
  
-   Непосредственно к видео портам на компьютере  
  
-   Через специализированные нуль-клиентов USB (также называемых многофункциональными концентраторами USB), а также через аналогичные устройства USB-over-Ethernet.  
  
-   По локальной сети (LAN)  
  
Каждый из этих методов более подробно описан в разделе [станции служб MultiPoint](MultiPoint-services-Stations.md) в этом документе.  
  
В этом документе рассматриваются следующие факторы, которые следует учитывать при планировании развертывания служб MultiPoint.  
  
-   Типы рабочих столов, которые следует использовать в системе служб MultiPoint: Вам понадобятся сеансы, виртуальные машины или компьютеры Windows?  
  
-   [Выбор оборудования для системы служб MultiPoint](Selecting-Hardware-for-Your-MultiPoint-services-System.md): Какие решения по оборудованию следует принять?  
  
-   [Требования к оборудованию и рекомендации по производительности](Hardware-Requirements-and-Performance-Recommendations.md): Какое оборудование требуется для служб MultiPoint?  
  
-   [Планирование сайтов служб MultiPoint](MultiPoint-services-Site-Planning.md): Где будут размещены компьютеры, на которых работают службы MultiPoint и их станции, и как они будут настроены?  
  
-   [Рекомендации по сети и учетные записи пользователей](Network-Considerations-and-User-Accounts.md): Сетевая среда, в которой развернута система служб MultiPoint, может влиять на управление учетными записями пользователей. Что такое сетевая среда? Как будут управляться учетными записями пользователей?  
  
-   [Хранение файлов с помощью служб MultiPoint](Storing-Files-with-MultiPoint-services.md): Где будут храниться файлы пользователей и как они будут доступны?  
  
-   [Контрольный список действий, выполняемых перед развертыванием](Predeployment-Checklist.md)  