---
title: Сбор драйверов оборудования и устройств, необходимых для установки
description: Сведения о драйверах, которые необходимо установить для служб MultiPoint
ms.custom: na
ms.prod: windows-server-threshold
ms.technology: multipoint-services
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4cf5fdbe-b871-4360-b003-d65ac43b491e
author: evaseydl
manager: scottman
ms.author: evas
ms.date: 08/04/2016
ms.openlocfilehash: f7fec373bc62c93fbf31bbb24bf1a11a42c0736d
ms.sourcegitcommit: f6490192d686f0a1e0c2ebe471f98e30105c0844
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70871427"
---
# <a name="collect-hardware-and-device-drivers-needed-for-the-installation"></a>Сбор драйверов оборудования и устройств, необходимых для установки
Прежде чем приступить к развертыванию системы служб MultiPoint, вам потребуется:  
  
-   **Компоненты оборудования для сервера** — установите в настоящее время дополнительные видеоадаптеры или другие системные компоненты.  
  
-   **Компоненты оборудования для станций** . сведения о станциях планирования для вашей среды см. в разделе [Выбор оборудования для системы служб MultiPoint](Selecting-Hardware-for-Your-MultiPoint-services-System.md).
-   **Последние версии драйверов для** видеоадаптеров. Если изготовитель оборудования или устройство не предоставил эти драйверы, их необходимо загрузить с веб-сайта изготовителя устройства.  
  
-   **Последние драйверы USB нуль-клиентов** . Если вы используете клиентские станции с нулевым числом портов USB, необходимо установить последние драйверы USB нуль Client.  
  
    > [!IMPORTANT]  
    > Для установки служб MultiPoint необходимо установить 64-разрядную версию всех драйверов.  
  
> [!TIP]  
> Если вы устанавливаете службы MultiPoint на компьютере с уже установленной другой версией Windows, то перед началом установки Windows Server следует узнать, что видеоадаптер и модель находятся в Device Manager до того, как вы сможете получить драйверы, которые доступно для Windows Server 2016. Откройте Device Manager, откройте окно " **Управление компьютером** " на **начальном** экране. Затем в дереве консоли щелкните **Device Manager**.