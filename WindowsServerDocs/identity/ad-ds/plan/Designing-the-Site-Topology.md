---
ms.assetid: eeb919de-e21e-48d8-8186-e42adec6933f
title: Проектирование топологии сайта
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: 23c80ffa3137f5609abdba9abea08ea62d305573
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86963796"
---
# <a name="designing-the-site-topology"></a>Проектирование топологии сайта

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Топология сайта службы каталогов — это логическое представление физической сети. Разработка топологии сайта для служб домен Active Directory (AD DS) предполагает планирование размещения контроллеров домена и проектирование сайтов, подсетей, связей сайтов и мостов связей сайтов для обеспечения эффективной маршрутизации трафика запросов и репликации.  
  
Создание топологии сайта помогает эффективно маршрутизировать запросы клиентов и Active Directory трафик репликации. Хорошо спроектированная топология сайта помогает Организации получить следующие преимущества:  
  
-   Сократите затраты на репликацию Active Directory данных.  
  
-   Сократите усилия по администрированию, необходимые для поддержки топологии сайта.  
  
-   Запланируйте репликацию, которая позволяет использовать медленные или коммутируемые сетевые соединения для репликации данных Active Directory в часы наименьшей нагрузки.  
  
-   Оптимизируйте способность клиентских компьютеров находить ближайшие ресурсы, такие как контроллеры домена и серверы распределенная файловая система (DFS). Это позволяет сократить сетевой трафик по медленным каналам глобальной сети, улучшить процессы входа в систему и выхода из системы и ускорить операции загрузки файлов.  
  
Прежде чем приступить к проектированию топологии сайтов, необходимо понимать структуру физической сети. Кроме того, сначала необходимо разработать логическую структуру Active Directory, включая административную иерархию, план леса и план домена для каждого леса. Необходимо также завершить структуру инфраструктуры службы доменных имен (DNS) для AD DS. Дополнительные сведения о проектировании логической структуры Active Directory и инфраструктуры DNS см. [в разделе Разработка логической структуры для Windows Server 2008 AD DS](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc770806(v=ws.10)).  
  
После завершения проектирования топологии сайта необходимо убедиться, что контроллеры домена соответствуют требованиям к оборудованию для Windows Server 2008 Standard, Windows Server 2008 Enterprise и Windows Server 2008 Datacenter.  
  
## <a name="in-this-guide"></a>В данном руководстве  
  
-   [Основные сведения о топологии сайта Active Directory](../../ad-ds/plan/Understanding-Active-Directory-Site-Topology.md)  
  
-   [Сбор сведений о сети](../../ad-ds/plan/Collecting-Network-Information.md)  
  
-   [Планирование размещения контроллеров доменов](../../ad-ds/plan/Planning-Domain-Controller-Placement.md)  
  
-   [Создание проекта сайта](../../ad-ds/plan/Creating-a-Site-Design.md)  
  
-   [Создание проекта связей сайтов](../../ad-ds/plan/Creating-a-Site-Link-Design.md)  
  
-   [Создание проекта моста связей сайтов](../../ad-ds/plan/Creating-a-Site-Link-Bridge-Design.md)  
  
-   [Поиск дополнительных ресурсов для архитектуры топологии сайта Windows Server 2008 Active Directory](../../ad-ds/plan/Finding-Additional-Resources-for-Windows-Server-2008-Active-Directory-Site-Topology-Design.md)  
  
