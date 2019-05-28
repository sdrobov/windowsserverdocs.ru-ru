---
ms.assetid: 9eab8c43-a0f2-4d19-a5a4-e1399f0d5f25
title: Определение стратегии работы с федеративными приложениями у партнера по ресурсам
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 15a6c095648795badfae6f68f1ba2f9270219db8
ms.sourcegitcommit: 0b5fd4dc4148b92480db04e4dc22e139dcff8582
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66191461"
---
# <a name="determine-your-federated-application-strategy-in-the-resource-partner"></a>Определение стратегии работы с федеративными приложениями у партнера по ресурсам

Важной частью проектирования новой службы федерации Active Directory \(AD FS\) инфраструктуру в организации партнера по ресурсам Определение полного набора приложений и служб, которые будут использоваться для участия в федерации и партнеров, учетной записи будут получателями этих ресурсов. Перед созданием стратегии работы с федеративными приложениями и службами ответьте на следующие вопросы.  
  
-   Будет иметь Включение и развертывание приложения ASP.NET или Windows Communication Foundation \(WCF\) службу федерации?  
  
-   Пользователям в корпоративной сети потребуется доступ к федеративному приложению или службе через систему встроенной аутентификации Windows?  
  
-   Федеративное приложение или служба будет использоваться пользователями в сети периметра? Если так, потребуется ли система встроенной аутентификации Windows?  
  
-   Все веб-серверов, на которых размещены федеративные приложения, под управлением операционной системы Windows Server и Internet Information Services \(IIS\)?  
  
-   Для кого будет предоставлять ресурсы федеративное приложение или служба?  
  
Ответы на эти вопросы помогут вам спланировать надежной архитектуры AD FS. Кроме того, это поможет в создании стратегии работы с федеративным приложением и службами, в основе которой лежат принципы экономичности и эффективного использования ресурсов. Дополнительные сведения о разработке оптимальной стратегии работы с федеративными приложениями и службами для вашей организации см. в следующих разделах этого руководства:  
  
-   [Предоставление пользователям Active Directory вашей организации доступа к вашим приложениям и службам с поддержкой утверждений](Provide-Your-Active-Directory-Users-Access-to-Your-Claims-Aware-Applications-and-Services.md)  
  
-   [Предоставление пользователям Active Directory вашей организации доступа к приложениям и службам других организаций](Provide-Your-Active-Directory-Users-Access-to-the-Applications-and-Services-of-Other-Organizations.md)  
  
-   [Предоставление пользователям другой организации доступа к вашим приложениям и службам с поддержкой утверждений](Provide-Users-in-Another-Organization-Access-to-Your-Claims-Aware-Applications-and-Services.md)  
  
Дополнительные сведения о создании утверждений\-приложение, работающее с ASP.NET или службы WCF, см. в разделе [Windows Identity Foundation SDK](https://go.microsoft.com/fwlink/?LinkId=122266).  
  
## <a name="see-also"></a>См. также
[Руководство по разработке служб федерации Active Directory в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)

