---
ms.assetid: 68979914-8a1c-465a-bd37-08df30722d69
title: Сопоставление целей развертывания с разработкой AD FS
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 048bce75c52895b2d9e215bdccef9cb13dc23533
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59866825"
---
# <a name="mapping-your-deployment-goals-to-an-ad-fs-design"></a>Сопоставление целей развертывания с разработкой AD FS

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Завершив просмотр существующих служб федерации Active Directory \(AD FS\) целей развертывания и определив цели, связанные с развертыванием, вы можете сопоставить эти цели по разработке AD FS. Дополнительные сведения о службах AD FS предварительно целей развертывания, см. в разделе [определение целей развертывания AD FS](Identifying-Your-AD-FS-Deployment-Goals.md).  
  
Используйте следующую таблицу, чтобы определить, какие зафиксированного дизайна AD FS сопоставляет подходящее сочетание AD FS целей развертывания для вашей организации. Эта таблица относится только два основной схемы AD FS, как описано в этом руководстве. Тем не менее можно создать гибридный или пользовательской системы AD FS, используя любую комбинацию целей развертывания AD FS в соответствии с потребностями вашей организации.  
  
|Цели развертывания AD FS|[Web SSO Design](Web-SSO-Design.md)|[Федеративного единого входа в Интернете](Federated-Web-SSO-Design.md)|  
|---------------------------------------------------------------------------|----------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|  
|[Предоставить пользователям доступ к Active Directory для приложений и служб](Provide-Your-Active-Directory-Users-Access-to-Your-Claims-Aware-Applications-and-Services.md)|Нет|Да, в партнере по учетным записям|  
|[Предоставить пользователям доступ к Active Directory к приложениям и службам других организаций](Provide-Your-Active-Directory-Users-Access-to-the-Applications-and-Services-of-Other-Organizations.md)|Нет|Да, возможно в партнере по учетным записям|  
|[Предоставление пользователям другой организации доступа к вашим приложениям с поддержкой утверждений и служб](Provide-Users-in-Another-Organization-Access-to-Your-Claims-Aware-Applications-and-Services.md)|Да|Да|  

## <a name="see-also"></a>См. также
[Руководство по разработке AD FS в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)
  

