---
title: Включить общий доступ к файлам
description: Сведения о совместном использовании файлов в службах MultiPoint
ms.date: 07/22/2016
ms.prod: windows-server
ms.technology: multipoint-services
ms.topic: article
ms.assetid: 508ad056-8e0c-4d59-a4fa-05775a54125d
author: evaseydl
ms.author: evas
manager: Scottman
ms.openlocfilehash: 73f89700228d912ac029a97dc3951be21a01e45a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80859267"
---
# <a name="enable-file-sharing-in-multipoint-services"></a>Включение совместного использования файлов в службах MultiPoint
Разрешить пользователям на ваших станциях MultiPoint общий доступ к файлам можно двумя способами:  
  
-   **Если в сети имеется файловый сервер,** рекомендуется создать общую папку на файловом сервере.  
  
-   **Если у вас небольшая сеть 2-3 MultiPoint Servers без выделенного файлового сервера,** один из серверов MultiPoint может работать в качестве файлового сервера для всех оставшихся компьютеров, на которых выполняются службы MultiPoint. Создайте общую папку на этом сервере, а затем создайте учетные записи локальных пользователей для всех пользователей на этом сервере. Общая папка может находиться на исходном внутреннем диске или присоединять к компьютеру дополнительные внутренние или внешние диски.  
  
