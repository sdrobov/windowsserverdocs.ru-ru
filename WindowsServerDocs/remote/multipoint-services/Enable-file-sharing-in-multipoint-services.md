---
title: Включить общий доступ к файлам
description: Дополнительные сведения о общий доступ к файлам в службах MultiPoint
ms.custom: na
ms.date: 07/22/2016
ms.prod: windows-server-threshold
ms.technology: multipoint-services
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 508ad056-8e0c-4d59-a4fa-05775a54125d
author: evaseydl
ms.author: evas
manager: Scottman
ms.openlocfilehash: e68fe300404456122012d11e8e164609c1af40b5
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59884845"
---
# <a name="enable-file-sharing-in-multipoint-services"></a>Включение совместного использования файлов в службах MultiPoint
Вы можете разрешить пользователям в вашей станций MultiPoint для совместного использования файлов двумя способами:  
  
-   **Если имеется файловый сервер в сети,** рекомендуется создать общую папку на файловом сервере.  
  
-   **При наличии небольших сетевых серверов MultiPoint 2 – 3, без сервера выделенном файле** один из серверов MultiPoint может действовать как файловый сервер для всех остальных компьютерах, выполняющих MultiPoint services. Создайте общую папку на этом сервере и затем создать локальные учетные записи пользователей для всех пользователей на этом сервере. Может быть общей папке на диске, внутренний исходный или на компьютер можно присоединить дополнительные диски внутренними или внешними.  
  
