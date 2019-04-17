---
ms.assetid: 68979914-8a1c-465a-bd37-08df30722d69
title: "Сопоставление целей развертывания с разработкой AD FS"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 048bce75c52895b2d9e215bdccef9cb13dc23533
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="mapping-your-deployment-goals-to-an-ad-fs-design"></a>Сопоставление целей развертывания с разработкой AD FS

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

После окончания просмотра существующих целей развертывания служб федерации Active Directory \(AD FS\) и определите цели, соответствующие вашему развертыванию, можно сопоставить эти цели для конкретных дизайна служб AD FS. Дополнительные сведения о службах AD FS предварительно целей развертывания, см. в разделе [определение целей развертывания AD FS](Identifying-Your-AD-FS-Deployment-Goals.md).  
  
Используйте следующую таблицу, чтобы определить, какие дизайна AD FS сопоставляется с соответствующей комбинацией AD FS целей развертывания для вашей организации. Эта таблица ссылается только двух основных проектов AD FS, как описано в данном руководстве. Тем не менее можно создать гибридный или пользовательской системы AD FS, используя любую комбинацию целей развертывания AD FS в соответствии с потребностями вашей организации.  
  
|Цель развертывания AD FS|[Web SSO Design](Web-SSO-Design.md)|[Федеративные Web SSO Design](Federated-Web-SSO-Design.md)|  
|---------------------------------------------------------------------------|----------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|  
|[Предоставлять пользователям доступ к Active Directory к поддерживающим утверждения приложениям и службам](Provide-Your-Active-Directory-Users-Access-to-Your-Claims-Aware-Applications-and-Services.md)|Нет|Да, в партнере по учетным записям|  
|[Предоставление Active Directory доступа пользователей к приложениям и службам других организаций](Provide-Your-Active-Directory-Users-Access-to-the-Applications-and-Services-of-Other-Organizations.md)|Нет|Да, возможно в партнере по учетным записям|  
|[Предоставление пользователям другой организации доступа к вашим поддерживающим утверждения приложениям и службам](Provide-Users-in-Another-Organization-Access-to-Your-Claims-Aware-Applications-and-Services.md)|Да|Да|  

## <a name="see-also"></a>См. также:
[Руководство по разработке служб AD FS в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)
  

