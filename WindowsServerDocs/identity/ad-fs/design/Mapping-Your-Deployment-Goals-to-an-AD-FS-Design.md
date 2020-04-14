---
ms.assetid: 68979914-8a1c-465a-bd37-08df30722d69
title: Сопоставление целей развертывания с разработкой AD FS
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 4154f46bdb1a7b3a2c81eba6882a6a095a16ee45
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80853057"
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
  

