---
ms.assetid: eb778f63-f7be-438e-8c5e-1fd9b194b967
title: Web SSO Design
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 1b8344594c9fc477ed8424c716ec8d7f7fd91ef3
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="web-sso-design"></a>Web SSO Design

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

В веб-разработки одиночных входа на \(SSO\) в \(AD FS\) служб федерации Active Directory пользователям необходимо пройти проверку подлинности только один раз для доступа к нескольким защищенным AD FS\ приложениям или службам. В этом проекте все пользователи являются внешними, и федеративное доверие отсутствует, так как нет партнерских организаций. Как правило этот проект разворачивается, когда требуется предоставить отдельному пользователю или клиенту доступ к одной или более AD FS защищаемому служб или приложений через Интернет, как показано на следующем рисунке.  
  
![Интернете [adfs2]](media/adfs2_WebSSODesign.gif)  
  
С помощью веб-служба SSO проекта, организация, которая обычно размещает AD FS\ защищенные приложения, или службу в сети периметра, может обслуживать отдельное хранилище учетных записей клиентов в сети периметра, что упрощает изоляцию учетных записей клиентов от учетных записей сотрудников.  
  
Можно управлять локальными учетными записями для клиентов в сети периметра с помощью либо \(AD DS\) доменных служб Active Directory, SQL Server или хранилища настраиваемых атрибутов.  
  
Такая структура совпадает с целью развертывания в [предоставляют Your Active Directory Users Access to Your Claims-Aware Applications and Services](Provide-Your-Active-Directory-Users-Access-to-Your-Claims-Aware-Applications-and-Services.md).  
  
Список подробных задач, которые можно использовать для планирования и развертывания проекта Единого входа см. в разделе [Checklist: Implementing a Web SSO Design](../../ad-fs/deployment/Checklist--Implementing-a-Web-SSO-Design.md).  
  
## <a name="see-also"></a>См. также:
[Руководство по разработке служб AD FS в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)
