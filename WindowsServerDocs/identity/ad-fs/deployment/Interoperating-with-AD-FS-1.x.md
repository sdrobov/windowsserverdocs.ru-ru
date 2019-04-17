---
ms.assetid: 97999892-29c6-4076-be19-5e5259d8ada6
title: "Развертывание серверов федерации"
description: 
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: f80425b6f062040c51357353038fd07ff0a79ae6
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="interoperating-with-ad-fs-1x"></a>Взаимодействие с AD FS 1.x

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Для обеспечения взаимодействия между \(AD FS\) служб федерации Active Directory в Windows Server® 2012 и AD FS 1. *x*, выполните одно или несколько из следующих действий в зависимости от потребностей вашей организации:  
  
-   Планирование взаимодействия между AD FS в Windows Server 2012 и предыдущие версии AD FS и узнать больше о идентификатор имени типа утверждения. Дополнительные сведения см. в разделе [планирование взаимодействия с AD FS 1.x](https://technet.microsoft.com/library/ff678040.aspx).  
  
-   Если вам будет отправлять утверждения из службы федерации AD FS в Windows Server 2012, которые могут использоваться службой AD FS 1. *x* службы федерации, в разделе [контрольный список: настройка AD FS to Send Claims to an AD FS 1.x Federation Service](Checklist--Configuring-AD-FS-to-Send-Claims-to-an-AD-FS-1.x-Federation-Service.md).  
  
-   Если вам будет отправлять утверждения из службы федерации AD FS в Windows Server 2012, которые могут использоваться приложением, размещенных на веб-сервер AD FS 1. *x* поддержкой claims\ веб-агент, см. [контрольный список: настройка AD FS to Send Claims to an AD FS 1.x Claims-Aware Web Agent](Checklist--Configuring-AD-FS-to-Send-Claims-to-an-AD-FS-1.x-Claims-Aware-Web-Agent.md).  
  
-   Если будут отправляться утверждений из AD FS 1. *x* службы федерации, используемый службой федерации AD FS в Windows Server 2012. в разделе [контрольный список: настройка AD FS для использования утверждений из AD FS 1.x](Checklist--Configuring-AD-FS--to-Consume-Claims-from-AD-FS-1.x.md).  
  
## <a name="differences-between-federation-service-settings"></a>Различия между параметрами службы федерации  
Несмотря на то что большинство из AD FS 1. *x* рабочих параметры службы федерации в так же, как службой федерации AD FS в Windows Server 2012 параметры, некоторые имена параметров были изменены. В следующей таблице перечислены имена параметров для AD FS 1. *x* службы федерации и именах эквивалент для службы федерации AD FS в Windows Server 2012.  
  
|AD FS 1.x службы федерации параметр|Эквивалентные службой федерации AD FS в Windows Server 2012 параметр  
|----------------------------------------|---------------------------------------------------------------------------------------------------------- 
|Партнер по учетным записям|Отношения доверия с поставщиком утверждений  
|Партнер по ресурсам|Проверяющей стороной доверия 
|Приложения|Проверяющей стороной доверия  
|Свойства приложения|Проверяющей стороной свойства отношений доверия  
|URL-адрес приложения|Проверяющей стороной идентификатор и наличия WS-Federation Endpoint URL-адрес пассивного  
|Служба федерации URI|Идентификатор службы федерации  
|URL-адрес конечной точки службы федерации|URL-адрес пассивной конечной точки наличия WS Federation  
  
## <a name="see-also"></a>См. также:  
[AD FS и AD FS 1.x взаимодействия](https://go.microsoft.com/fwlink/?LinkId=200776)  
  

