---
ms.assetid: eeb919de-e21e-48d8-8186-e42adec6933f
title: "Проектирование топологии сайта"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 3f16b5b941ef9c3bd8f4bf742d432afc1b3f559a
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="designing-the-site-topology"></a>Проектирование топологии сайта

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Топология сайта службы каталогов — это логическое представление физической сети. Проектирование топологии сайта для доменных служб Active Directory (AD DS) включает в себя планирование размещения контроллера домена и разработка сайтов, подсетей, связи сайтов и мосты связей сайтов, чтобы обеспечить эффективную маршрутизацию трафика запросов и репликации.  
  
Проектирование топологии сайта поможет вам эффективно направлять запросы клиентов и трафик репликации Active Directory. Хорошо спроектированное топологией поможет организации получить следующие преимущества:  
  
-   Сократить расходы на репликацию данных Active Directory.  
  
-   Свести к минимуму административные усилия, необходимые для поддержания топологии сайта.  
  
-   Запланируйте репликацию, которая позволяет расположения ссылки медленной или удаленный доступ к сети для репликации данных Active Directory во время наименьшей нагрузки.  
  
-   Оптимизируйте возможность клиентских компьютеров, найдите ближайший ресурсов, таких как контроллеры домена и серверы распределенной файловой системы (DFS). Это позволяет сократить сетевой трафик по медленному каналу глобальной сети (WAN) ссылки, улучшения процессы входа и выхода и ускорить операции с файлами загрузки.  
  
Прежде чем начать для проектирования топологии сайтов, необходимо представлять себе структуру физической сети. Кроме того необходимо сначала создать вашей логической структуры Active Directory, включая административные иерархии, плана леса и домена плана для каждого леса. Необходимо также выполнить разработки инфраструктуры вашей системы доменных имен (DNS) для службы AD DS. Дополнительные сведения о разработке логической структуры Active Directory и инфраструктуры DNS см. в разделе [проектирование логической структуры для Windows Server 2008 службы AD DS](https://technet.microsoft.com/library/cc770806.aspx).  
  
После завершения вашего проектирование топологии сайта необходимо убедиться, что контроллеры домена удовлетворяют требованиям к оборудованию для Windows Server 2008 Standard, Windows Server 2008 Enterprise и Windows Server 2008 Datacenter.  
  
## <a name="in-this-guide"></a>В этом руководстве  
  
-   [Основные сведения о топологии сайта Active Directory](../../ad-ds/plan/Understanding-Active-Directory-Site-Topology.md)  
  
-   [Сбор сведений о сети](../../ad-ds/plan/Collecting-Network-Information.md)  
  
-   [Планирование размещения контроллера домена](../../ad-ds/plan/Planning-Domain-Controller-Placement.md)  
  
-   [Создание проекта сайта](../../ad-ds/plan/Creating-a-Site-Design.md)  
  
-   [Создание проекта связей сайтов](../../ad-ds/plan/Creating-a-Site-Link-Design.md)  
  
-   [Создание проекта моста связей сайтов](../../ad-ds/plan/Creating-a-Site-Link-Bridge-Design.md)  
  
-   [Поиск дополнительных ресурсов для проектирования топологии сайтов 2008 Active Directory Server Windows](../../ad-ds/plan/Finding-Additional-Resources-for-Windows-Server-2008-Active-Directory-Site-Topology-Design.md)  
  


