---
ms.assetid: eb778f63-f7be-438e-8c5e-1fd9b194b967
title: Проект единого входа через Интернет
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 1b8344594c9fc477ed8424c716ec8d7f7fd91ef3
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59852805"
---
# <a name="web-sso-design"></a>Проект единого входа через Интернет

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

В одном Web\-входа\-на \(SSO\) разработки в службах федерации Active Directory \(AD FS\), пользователи должны проходить проверку подлинности только один раз для доступа к нескольким AD FS\- защищенных приложений или служб. В этом проекте все пользователи являются внешними, и федеративное доверие отсутствует, так как нет партнерских организаций. Как правило этот проект разворачивается, когда вы хотите предоставить отдельных потребителей или клиенту доступ к одной или более AD FS — защищенных служб или приложений в Интернете, как показано на следующем рисунке.  
  
![единый вход в Интернете](media/adfs2_WebSSODesign.gif)  
  
С помощью единого входа в Интернете организация, обычно размещает AD FS\-защищенного приложения или службы в сети периметра может обслуживать отдельное хранилище учетных записей клиентов в сети периметра, что упрощает для изоляции клиентов учетные записи от учетных записей сотрудников.  
  
Можно управлять локальными учетными записями для клиентов в сети периметра с помощью доменные службы Active Directory \(AD DS\), SQL Server или хранилища настраиваемых атрибутов.  
  
Такая структура совпадает с целью развертывания в [Provide Your Active Directory Users Access to Your Claims-Aware Applications and Services](Provide-Your-Active-Directory-Users-Access-to-Your-Claims-Aware-Applications-and-Services.md).  
  
Список подробных задач, которые можно использовать для планирования и развертывания проекта единого входа через Интернет, см. в разделе [контрольный список: Реализация единого входа в Интернете](../../ad-fs/deployment/Checklist--Implementing-a-Web-SSO-Design.md).  
  
## <a name="see-also"></a>См. также
[Руководство по разработке AD FS в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)
