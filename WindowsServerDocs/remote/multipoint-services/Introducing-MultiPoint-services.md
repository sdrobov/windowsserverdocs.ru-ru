---
title: Основные сведения о службах MultiPoint
description: Содержит общие сведения о службах MultiPoint, способах предоставления общего доступа к системе нескольким пользователям.
ms.date: 07/22/2016
ms.prod: windows-server
ms.technology: multipoint-services
ms.topic: article
ms.assetid: 1cbef744-4661-4ba9-9e2b-0bbd8854fd5c
author: evaseydl
manager: scottman
ms.author: evas
ms.openlocfilehash: e547156bb46d7195baa64a0094f1d3ca432eb016
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80859177"
---
# <a name="introducing-multipoint-services"></a>Основные сведения о службах MultiPoint
Роль служб MultiPoint в Windows Server 2016 позволяет нескольким пользователям с собственными независимыми и привычными возможностями Windows совместно использовать один компьютер. Существует несколько способов доступа пользователей к своим сеансам. Один из способов — удаленное взаимодействие с сервером с помощью [приложений удаленного рабочего стола](../remote-desktop-services/clients/remote-desktop-clients.md) с любым устройством. Другой способ — благодаря физическим станциям, подключенным к серверу MultiPoint:  
  
-   Непосредственно к видео портам на компьютере  
  
-   Через специализированные нуль-клиентов USB (также называемых многофункциональными концентраторами USB), а также через аналогичные устройства USB-over-Ethernet.  
  
-   По локальной сети (LAN)  
  
Каждый из этих методов более подробно описан в разделе [станции служб MultiPoint](MultiPoint-services-Stations.md) в этом документе.  
  
В этом документе рассматриваются следующие факторы, которые следует учитывать при планировании развертывания служб MultiPoint.  
  
-   Какие типы настольных компьютеров будут использоваться в системе служб MultiPoint: требуются ли сеансы, виртуальные машины или компьютеры Windows?  
  
-   [Выбор оборудования для системы служб MultiPoint](Selecting-Hardware-for-Your-MultiPoint-services-System.md): какие решения должно быть принято?  
  
-   [Требования к оборудованию и рекомендации по производительности](Hardware-Requirements-and-Performance-Recommendations.md): какое оборудование требуется для служб MultiPoint?  
  
-   [Планирование сайтов служб MultiPoint](MultiPoint-services-Site-Planning.md). где будут размещаться компьютеры, на которых работают службы MultiPoint и их станции, и как они будут настроены?  
  
-   [Рекомендации по сети и учетные записи пользователей](Network-Considerations-and-User-Accounts.md). Сетевая среда, в которой развернута система служб MultiPoint, может влиять на управление учетными записями пользователей. Что такое сетевая среда? Как будут управляться учетными записями пользователей?  
  
-   [Хранение файлов с помощью служб MultiPoint](Storing-Files-with-MultiPoint-services.md): где будут храниться файлы пользователей и как они будут доступны?  
  
-   [Контрольный список действий, выполняемых перед развертыванием](Predeployment-Checklist.md)  