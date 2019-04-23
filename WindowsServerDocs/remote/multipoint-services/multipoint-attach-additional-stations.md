---
title: Присоединить дополнительные станции к серверу MultiPoint
description: Добавить дополнительные станции MultiPoint Services развертывание
ms.custom: na
ms.prod: windows-server-threshold
ms.technology: multipoint-services
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d78ebf4e-0968-4014-9a42-9f75cc50cb52
author: evaseydl
manager: scottman
ms.author: evas
ms.date: 08/04/2016
ms.openlocfilehash: 57fc8ed6774c3266298ecd98e8f609ec01f63ef6
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59889265"
---
# <a name="attach-additional-stations-to-multipoint-services"></a>Присоединить дополнительные станции MultiPoint Services
В вашей среде MultiPoint Services пользователи использовать станции для подключения к MultiPoint Services и выполнять свою работу. Станции являются конечными точками пользователя для подключения к компьютеру с запущенной Multipoint Services.  
  
MultiPoint services поддерживает три режима станции:  
  
-   Станций, подключенных напрямую видео  
  
-   USB нуля клиент подключен станции (и USB на станции клиенту, подключившемуся Ethernet ноль)  
  
-   Станции, подключенные к RDP через Локальную  
  
Классификации основаны на оборудованием станции и тип соединения, который его использует. Вы можно комбинировать и сопоставлять типы подключений для вашей станций. Единственным требованием является то, что главная станция (который ранее установленный) должен быть станции подключенных напрямую видео. Дополнительные сведения о настройках станции см. в разделе [станции MultiPoint](MultiPoint-services-Stations.md).  
  
Инструкции, поясняющие, как настроить каждый тип станции см. в разделе ниже:  
  
-   [Создание станции подключенных напрямую видео](Set-up-a-direct-video-connected-station-in-MultiPoint-services.md)  
  
-   [Настройка USB ноль станции клиент подключен](Set-up-a-USB-zero-client-connected-station-in-MultiPoint-services.md)  
  
-   [Станции RDP через Локальную подключен](Set-up-an-RDP-over-LAN-connected-station-in-MultiPoint-services.md)  
  
Более подробное сравнение типов станции см. в разделе [сравнение типов станции](multipoint-services-stations.md#BKMK_StationTypeComparison).  
  
> [!NOTE]  
> -   Для присоединения станции не описано, как настроить промежуточные центры или нисходящие концентраторы. Сведения о месте установки этих центров, см. в разделе [станции MultiPoint](MultiPoint-services-Stations.md).  
> -   В некоторых случаях может потребоваться создать станции виртуальных рабочих столов, которые выполняются на виртуальных машинах. Например использовать приложения, которые нельзя устанавливать на сервере Windows или приложений, которые не будут выполняться несколько экземпляров на одном главном компьютере. Дополнительные сведения см. в разделе [виртуальные рабочие столы Создание Windows 10 Корпоративная для станций](Create-Windows-10-Enterprise-virtual-desktops-for-stations.md).  
  
> [!TIP]  
> Это полезно для создания вашего станций в порядке их физического расположения, таким образом, чтобы они последовательно определены в MultiPoint Server. Если позже вы хотите изменить имя станции, это можно сделать в MultiPoint Manager. Дополнительные сведения см. в разделе сопоставления всех станций в MultiPoint Server справки и поддержки.