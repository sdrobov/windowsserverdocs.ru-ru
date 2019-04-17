---
ms.assetid: 9eab8c43-a0f2-4d19-a5a4-e1399f0d5f25
title: "Определение стратегии работы с федеративными приложениями в организации партнера по ресурсам"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: aca47658cc5a20f63dbd59a26ebe135dd04def92
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="determine-your-federated-application-strategy-in-the-resource-partner"></a>Определение стратегии работы с федеративными приложениями в организации партнера по ресурсам

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Важной частью проектирования новой инфраструктуры \(AD FS\) служб федерации Active Directory в организации партнера по ресурсам Определение полного набора приложений и служб, который будет использоваться для участия в федерации, и какие партнеров по учетным записям будут получателями этих ресурсов. Перед созданием стратегии работы с федеративными приложениями и службами, ответьте на следующие вопросы:  
  
-   Будет включение и развертывании ASP.NET приложения или службы Windows Communication Foundation \(WCF\) для федерации?  
  
-   Пользователям в корпоративной сети потребуется доступ к федеративному приложению или службе через систему встроенной аутентификации Windows?  
  
-   Будет Федеративное приложение или служба будет использоваться пользователями в сети периметра? В этом случае встроенную проверку подлинности Windows будут необходимы?  
  
-   Все веб-серверы являются которых размещены федеративные приложения, работающих под управлением операционной системы Windows Server и служб Internet Information Services \(IIS\)?  
  
-   Кто будет Федеративное приложение или служба предоставлять ресурсы для?  
  
Ответы на эти вопросы помогут вам спланировать сплошной дизайна служб AD FS. Также это поможет в создании эффективного с федеративными приложениями и службы стратегии, согласно которой лежат принципы экономичности и ресурсов. Дополнительные сведения о разработке наиболее подходящий федеративными приложениями и службами стратегии вашей организации см. следующие разделы этого руководства:  
  
-   [Предоставлять пользователям доступ к Active Directory к поддерживающим утверждения приложениям и службам](Provide-Your-Active-Directory-Users-Access-to-Your-Claims-Aware-Applications-and-Services.md)  
  
-   [Предоставление Active Directory доступа пользователей к приложениям и службам других организаций](Provide-Your-Active-Directory-Users-Access-to-the-Applications-and-Services-of-Other-Organizations.md)  
  
-   [Предоставление пользователям другой организации доступа к вашим поддерживающим утверждения приложениям и службам](Provide-Users-in-Another-Organization-Access-to-Your-Claims-Aware-Applications-and-Services.md)  
  
Дополнительные сведения о создании приложения с поддержкой claims\ ASP.NET или службы WCF см. в разделе [Windows Identity Foundation SDK](https://go.microsoft.com/fwlink/?LinkId=122266).  
  
## <a name="see-also"></a>См. также:
[Руководство по разработке служб AD FS в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)

