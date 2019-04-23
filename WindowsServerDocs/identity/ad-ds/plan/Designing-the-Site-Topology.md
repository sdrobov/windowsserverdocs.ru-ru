---
ms.assetid: eeb919de-e21e-48d8-8186-e42adec6933f
title: Проектирование топологии сайта
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: e1d9323ceda478369973f959687d46c9ca3cb88f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59888495"
---
# <a name="designing-the-site-topology"></a>Проектирование топологии сайта

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Топология сайта службы каталогов — это логическое представление физической сети. Проектирование топологии сайта для доменных служб Active Directory (AD DS) включает в себя планирование размещение контроллера домена и проектирование сайтов, подсетей, связи сайтов и мосты связей сайтов, чтобы обеспечить эффективную маршрутизацию трафика запросов и репликации.  
  
Проектирование топологии сайта помогает эффективно направлять запросы клиента и трафика репликации Active Directory. Хорошо спроектированный топологией поможет вашей организации следующие преимущества:  
  
-   Свести к минимуму затраты на репликацию данных Active Directory.  
  
-   Свести к минимуму административные усилия, необходимые для поддержки топологии сайта.  
  
-   Запланируйте репликацию, позволяющий расположений со ссылками медленное или коммутируемое сетевое для репликации данных Active Directory в часы наименьшей нагрузки.  
  
-   Оптимизируйте возможности клиентских компьютеров для поиска ближайшего ресурсов, таких как контроллеры домена и серверы распределенной файловой системы (DFS). Помогает сократить сетевой трафик через медленные сетевые соединения (WAN), улучшения процессов входа в систему и выхода из системы и ускорить операции загрузки файла.  
  
Перед началом проектирования топологии сайтов, необходимо понимать структуру физической сети. Кроме того необходимо сначала разработать логической структуры Active Directory, включая административные иерархии, план леса и домена план для каждого леса. Необходимо также выполнить конструкции вашей инфраструктуры доменных имен (DNS) для AD DS. Дополнительные сведения о разработке логической структуры службы Active Directory и инфраструктуры DNS, см. в разделе [проектирование логической структуры для Windows Server 2008 AD DS](https://technet.microsoft.com/library/cc770806.aspx).  
  
После завершения проекта веб-узла топологии, необходимо убедиться, что контроллеры домена удовлетворяют требования к оборудованию для Windows Server 2008 Standard, Windows Server 2008 Enterprise и Windows Server 2008 Datacenter.  
  
## <a name="in-this-guide"></a>В данном руководстве  
  
-   [Основные сведения о топологии сайтов Active Directory](../../ad-ds/plan/Understanding-Active-Directory-Site-Topology.md)  
  
-   [Сбор сведений о сети](../../ad-ds/plan/Collecting-Network-Information.md)  
  
-   [Планирование размещения контроллеров доменов](../../ad-ds/plan/Planning-Domain-Controller-Placement.md)  
  
-   [Создание проекта сайта](../../ad-ds/plan/Creating-a-Site-Design.md)  
  
-   [Создание проекта связей сайтов](../../ad-ds/plan/Creating-a-Site-Link-Design.md)  
  
-   [Создание проекта моста связей сайтов](../../ad-ds/plan/Creating-a-Site-Link-Bridge-Design.md)  
  
-   [Поиск дополнительных ресурсов для проектирования топологии сайтов сервера Windows Server 2008 Active Directory](../../ad-ds/plan/Finding-Additional-Resources-for-Windows-Server-2008-Active-Directory-Site-Topology-Design.md)  
  


