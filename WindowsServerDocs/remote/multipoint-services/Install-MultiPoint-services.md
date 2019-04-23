---
title: Установка служб MultiPoint
description: Узнайте, как установить и настроить MultiPoint Services в Windows Server 2016
ms.custom: na
ms.date: 07/22/2016
ms.prod: windows-server-threshold
ms.technology: multipoint-services
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f6f8970b-de3f-4255-b2a1-5472a16ed02f
author: evaseydl
manager: scottman
ms.author: evas
ms.openlocfilehash: 52a824bbca3e9f2e1c7823601f6208ae19ae50ef
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59866225"
---
# <a name="install-multipoint-services"></a>Установка служб MultiPoint
Если вы устанавливаете сервер с нуля, выполните следующие действия для установки служб MultiPoint.  

После установки Windows Server 2016 успешно войти в систему от имени администратора. С помощью диспетчера серверов, где вы можете включить MultiPoint Services. Диспетчер сервера автоматически открывается при запуске. На панели мониторинга выберите **Добавить роли и компоненты** для включения служб MultiPoint и следуйте инструкциям в мастере.

В разделе для типа установки может открыться с помощью 
- Установка ролей или компонентов или
- Удаленную установку службы рабочего стола

Для развертывания стандартных MultiPoint Services рекомендуется выбрать установку служб удаленных рабочих столов, который позволяет легко выбрать роль MultiPoint Services в качестве типа развертывания. Для установки ролей необходимо выбрать **MultiPoint Services** в списке ролей. После успешной установки приведет к перезагрузке сервера.  
  
## <a name="configure-your-primary-station"></a>Настройка вашей основной станции  
  
1.  На **создания станции MultiPoint Server** введите указанного письма с помощью клавиатуры для этого монитора. Правильный ввод ключа связывает клавиатуру и мышь для этой станции.  
2.  Войдите в систему как администратор.  