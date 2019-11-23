---
ms.assetid: 68979914-8a1c-465a-bd37-08df30722d69
title: Сопоставление целей развертывания с разработкой AD FS
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: ca10f8e784fea3b99a60b2117f65ba1ccaf6501e
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71359089"
---
# <a name="mapping-your-deployment-goals-to-an-ad-fs-design"></a>Сопоставление целей развертывания с разработкой AD FS


После того как вы просматриваете существующие службы федерации Active Directory (AD FS) \(AD FS\) целей развертывания и определяете, какие цели связаны с развертыванием, вы можете сопоставлять эти цели с определенной структурой AD FS. Дополнительные сведения о AD FS предопределенных целей развертывания см. [в разделе Определение целей развертывания AD FS](Identifying-Your-AD-FS-Deployment-Goals.md).  
  
Используйте следующую таблицу, чтобы определить, какая AD FS схема сопоставляется с соответствующим сочетанием AD FS целей развертывания для вашей организации. Эта таблица относится только к двум основным AD FSным проектам, как описано в этом разделе. Однако вы можете создать гибридную или настраиваемую структуру AD FS, используя любое сочетание целей развертывания AD FS в соответствии с потребностями Организации.  
  
|Цель развертывания AD FS|[Проект единого входа через Интернет](Web-SSO-Design.md)|[Проект единого входа федерации для интернет-решений](Federated-Web-SSO-Design.md)|  
|---------------------------------------------------------------------------|----------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|  
|[Предоставление пользователям Active Directory вашей организации доступа к вашим приложениям и службам с поддержкой утверждений](Provide-Your-Active-Directory-Users-Access-to-Your-Claims-Aware-Applications-and-Services.md)|Нет|Да, в партнере по учетным записям|  
|[Предоставление пользователям Active Directory вашей организации доступа к приложениям и службам других организаций](Provide-Your-Active-Directory-Users-Access-to-the-Applications-and-Services-of-Other-Organizations.md)|Нет|Да, возможно в партнере по учетным записям|  
|[Предоставление пользователям другой организации доступа к вашим приложениям и службам с поддержкой утверждений](Provide-Users-in-Another-Organization-Access-to-Your-Claims-Aware-Applications-and-Services.md)|Да|Да|  

## <a name="see-also"></a>См. также
[Руководство по разработке служб федерации Active Directory в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)
  

