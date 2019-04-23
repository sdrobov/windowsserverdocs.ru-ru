---
title: Основные сведения о службах MultiPoint
description: Общие сведения о службах MultiPoint нескольким пользователям возможность совместного использования системы
ms.custom: na
ms.date: 07/22/2016
ms.prod: windows-server-threshold
ms.technology: multipoint-services
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1cbef744-4661-4ba9-9e2b-0bbd8854fd5c
author: evaseydl
manager: scottman
ms.author: evas
ms.openlocfilehash: 86d240092282e7cc29eebe638e5a97312e22baff
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59844215"
---
# <a name="introducing-multipoint-services"></a>Основные сведения о службах MultiPoint
Роль multiPoint Services в Windows Server 2016 позволяет нескольким пользователям, каждый из которых собственные независимые, знакомый Windows опыта, одновременно на одном компьютере общую папку. Существует несколько способов, которые пользователи могут обращаться к их сеансы. Один из способов — при удаленном взаимодействии на сервер, используя [удаленного рабочего стола приложения](../remote-desktop-services/clients/remote-desktop-clients.md) с любого устройства. Другим способом является через станции подключен к серверу MultiPoint физических станции:  
  
-   Непосредственно на видео портов на компьютере  
  
-   Специализированные клиентов USB zero (называемый также многофункциональные концентраторы USB), а также через подобных устройств для USB через Ethernet.  
  
-   По локальной сети (LAN)  
  
Каждый из этих методов описан более подробно в [станции MultiPoint Services](MultiPoint-services-Stations.md) далее в этом документе.  
  
В этом документе рассматриваются следующие факторы, которые следует учитывать при планировании для развертывания служб MultiPoint:  
  
-   Какой тип настольных компьютеров для использования с системой MultiPoint Services: Потребуется ли сеансы, виртуальных машин или компьютеров Windows?  
  
-   [Выбор оборудования для системы MultiPoint Services](Selecting-Hardware-for-Your-MultiPoint-services-System.md): Какое оборудование следует решения, принимаемые?  
  
-   [Требования к оборудованию и рекомендации по повышению производительности](Hardware-Requirements-and-Performance-Recommendations.md): Какое оборудование требуется для служб MultiPoint?  
  
-   [Планирование сайта служб multiPoint](MultiPoint-services-Site-Planning.md): Где компьютеров, работающих под управлением MultiPoint Services и их станции будут размещены и как они будут настраиваться?  
  
-   [Вопросы и учетные записи пользователей сети](Network-Considerations-and-User-Accounts.md): Сетевой среды, в которую развертывается система MultiPoint Services может влиять на управление учетными записями пользователей. Что такое сетевой средой? Как будет осуществляться управление учетными записями пользователей?  
  
-   [Хранение файлов вместе с MultiPoint Services](Storing-Files-with-MultiPoint-services.md): Пользовательские файлы хранения, и как они будут осуществляться?  
  
-   [Контрольный список перед развертыванием](Predeployment-Checklist.md)  