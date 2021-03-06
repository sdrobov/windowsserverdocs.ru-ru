---
title: Настройка общих подключений для всех пользователей шлюза Windows Admin Center
description: Узнайте о том, как администраторам достаточно один раз настроить шлюз Windows Admin Center (Project Honolulu), чтобы предоставить всем пользователям единый список подключений.
ms.technology: manage
ms.topic: article
author: haley-rowland
ms.author: harowl
ms.date: 03/28/2019
ms.localizationpriority: medium
ms.prod: windows-server
ms.openlocfilehash: e0e78ac8feb4e008e060ba318bd5693e841b91b2
ms.sourcegitcommit: 3632b72f63fe4e70eea6c2e97f17d54cb49566fd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2020
ms.locfileid: "87518601"
---
# <a name="configure-shared-connections-for-all-users-of-the-windows-admin-center-gateway"></a>Настройка общих подключений для всех пользователей шлюза Windows Admin Center

> Область применения. Windows Admin Center (ознакомительная версия), Windows Admin Center

Благодаря возможности настройки общих подключений администраторам шлюза достаточно один раз подготовить список подключений для всех пользователей определенного шлюза Windows Admin Center. Эта функция доступна только в режиме службы Windows Admin Center.

В разделе настроек шлюза Windows Admin Center есть вкладка **Shared Connections** (Общие подключения), где администраторы шлюза могут добавлять конфигурации подключения серверов, кластеров и ПК так же, как на странице всех подключений, включая возможность указывать теги подключений. Все подключения и теги, добавленные в список общих подключений, будут отображаться на странице всех подключений для всех пользователей этого шлюза Windows Admin Center.

![Windows Admin Center — страница Shared Connections (Общие подключения)](../media/shared-cnxns-1.png)

После настройки общих подключений на странице всех подключений для пользователей Windows Admin Center отобразятся подключения, сгруппированные в два раздела: персональные подключения и общие подключения. В разделе персональных подключений содержится список подключений определенного пользователя, которые сохраняются в сеансах браузера этого пользователя. Раздел общих подключений будет одинаковым для всех пользователей. Список подключений из этого раздела нельзя изменить на странице всех подключений.

![Windows Admin Center — страница "Все подключения"](../media/shared-cnxns-2.png)