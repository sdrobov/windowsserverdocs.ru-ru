---
title: Установка служб MultiPoint
description: Узнайте, как установить и настроить службы MultiPoint в Windows Server 2016
ms.custom: na
ms.date: 07/22/2016
ms.prod: windows-server
ms.technology: multipoint-services
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f6f8970b-de3f-4255-b2a1-5472a16ed02f
author: evaseydl
manager: scottman
ms.author: evas
ms.openlocfilehash: 442699afe40ee67e4cd4f13572d1a482f675b84a
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71395380"
---
# <a name="install-multipoint-services"></a>Установка служб MultiPoint
При установке сервера с нуля следуйте этим инструкциям, чтобы установить службы MultiPoint.  

После установки Windows Server 2016 успешно Войдите в систему от имени администратора. Используйте диспетчер сервера, где можно включить службы MultiPoint. Диспетчер сервера открывается автоматически при запуске. На панели мониторинга выберите **Добавить роли и компоненты** , чтобы включить службы MultiPoint, и следуйте инструкциям мастера.

В разделе, посвященном типу установки, можно выполнить команду 
- Установка на основе ролей или компонентов или
- Установка службы удаленных рабочих столов

Для стандартных развертываний служб MultiPoint рекомендуется выбрать установку службы удаленных рабочих столов, которая позволяет легко выбрать роль служб MultiPoint в разделе Тип развертывания. Для установки на основе ролей потребуется выбрать **службы MultiPoint** в списке ролей. После успешной установки сервер будет перезагружен.  
  
## <a name="configure-your-primary-station"></a>Настройка основной станции  
  
1.  На странице **Создание станции MultiPoint Server** введите указанную букву с клавиатуры для этого монитора. Правильная запись ключа связывает клавиатуру и мышь для этой станции.  
2.  Войдите в систему от имени администратора.  