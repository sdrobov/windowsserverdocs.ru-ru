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
ms.openlocfilehash: 13d8ae8b8f3e4c8160f61284e5fb97e21b6a51b6
ms.sourcegitcommit: 0b5fd4dc4148b92480db04e4dc22e139dcff8582
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66191251"
---
# <a name="mapping-your-deployment-goals-to-an-ad-fs-design"></a>Сопоставление целей развертывания с разработкой AD FS


Завершив просмотр существующих служб федерации Active Directory \(AD FS\) целей развертывания и определив цели, связанные с развертыванием, вы можете сопоставить эти цели по разработке AD FS. Дополнительные сведения о службах AD FS предварительно целей развертывания, см. в разделе [определение целей развертывания AD FS](Identifying-Your-AD-FS-Deployment-Goals.md).  
  
Используйте следующую таблицу, чтобы определить, какие зафиксированного дизайна AD FS сопоставляет подходящее сочетание AD FS целей развертывания для вашей организации. Эта таблица относится только два основной схемы AD FS, как описано в этом руководстве. Тем не менее можно создать гибридный или пользовательской системы AD FS, используя любую комбинацию целей развертывания AD FS в соответствии с потребностями вашей организации.  
  
|Цели развертывания AD FS|[Проект единого входа через Интернет](Web-SSO-Design.md)|[Проект единого входа федерации для интернет-решений](Federated-Web-SSO-Design.md)|  
|---------------------------------------------------------------------------|----------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|  
|[Предоставление пользователям Active Directory вашей организации доступа к вашим приложениям и службам с поддержкой утверждений](Provide-Your-Active-Directory-Users-Access-to-Your-Claims-Aware-Applications-and-Services.md)|Нет|Да, в партнере по учетным записям|  
|[Предоставление пользователям Active Directory вашей организации доступа к приложениям и службам других организаций](Provide-Your-Active-Directory-Users-Access-to-the-Applications-and-Services-of-Other-Organizations.md)|Нет|Да, возможно в партнере по учетным записям|  
|[Предоставление пользователям другой организации доступа к вашим приложениям и службам с поддержкой утверждений](Provide-Users-in-Another-Organization-Access-to-Your-Claims-Aware-Applications-and-Services.md)|Да|Да|  

## <a name="see-also"></a>См. также
[Руководство по разработке служб федерации Active Directory в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)
  

