---
ms.assetid: 04b63d9f-e924-4146-9b1d-785ed8b4239c
title: "Планирование взаимодействия с AD FS 1.x"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: f287261ce6cb56e40385ef4de922045153819a23
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="planning-for-interoperability-with-ad-fs-1x"></a>Планирование взаимодействия с AD FS 1.x

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Серверы федерации \(AD FS\) для Active Directory службы федерации под управлением Windows Server® 2012, могут взаимодействовать с обоих AD FS 1.0 \ (установленными с Windows Server 2003 R2\) службы федерации и AD FS 1.1 \ (установленными с Windows Server 2008 или Windows Server 2008 R2\) службы федерации. Поддерживаются любые из указанных ниже сочетаний.  
  
-   Любой AD FS 1. *x* службы федерации можно отправлять утверждения, которые могут использоваться службой федерации AD FS в Windows Server 2012. Дополнительные сведения см. в разделе [контрольный список: настройка AD FS для использования утверждений из AD FS 1.x](../../ad-fs/deployment/Checklist--Configuring-AD-FS--to-Consume-Claims-from-AD-FS-1.x.md).  
  
-   Любой службой федерации AD FS в Windows Server 2012 может отправлять AD FS 1. *x*\-compatible утверждения, которые могут использоваться службой AD FS 1. *x* службы федерации. Дополнительные сведения см. в разделе [контрольный список: настройка AD FS to Send Claims to an AD FS 1.x Federation Service](../../ad-fs/deployment/Checklist--Configuring-AD-FS-to-Send-Claims-to-an-AD-FS-1.x-Federation-Service.md).  
  
-   Любой службой федерации AD FS в Windows Server 2012 может отправлять AD FS 1. *x*\-compatible утверждения, которые могут использоваться для одного или нескольких веб-серверов под управлением AD FS 1. *x* поддержкой claims\ веб-агент. Дополнительные сведения см. в разделе [контрольный список: настройка AD FS to Send Claims to an AD FS 1.x Claims-Aware Web Agent](../../ad-fs/deployment/Checklist--Configuring-AD-FS-to-Send-Claims-to-an-AD-FS-1.x-Claims-Aware-Web-Agent.md).  
  
> [!NOTE]  
> Службы федерации Active Directory не поддерживает и взаимодействии с AD FS 1. *x* Windows NT на основе токенов веб-агент.  
  
AD FS 1. *x*\-compatible утверждения является утверждения, отправляемые службой федерации AD FS в Windows Server 2012 и понятны AD FS 1. *x* службы федерации. Таким образом, что AD FS 1. *x* службы федерации могла принимать утверждения, отправляемые службой федерации AD FS, тип утверждения идентификатора имени \(ID\) должны отправляться.  
  
## <a name="understanding-the-name-id-claim-type"></a>Сведения о типе утверждений идентификатор имени  
Тип утверждения идентификатора имени, введите эквивалент утверждений удостоверений, AD FS 1. *x* uses. Он должен использоваться при любом взаимодействии с AD FS 1. *x*. Утверждения идентификатора имени введите позволяет либо AD FS 1. *x* службы федерации или AD FS 1. *x* поддержкой claims\ веб-агент использовать утверждения, AD FS в Windows Server 2012, до тех пор, пока эти утверждения отправляются в одном из перечисленных форматов идентификатор имени в следующей таблице.  
  
|Формат идентификатора имени|Соответствующий код URI|  
|------------------|---------------------|  
|AD FS 1. *x* адрес электронной почты|http://schemas.xmlsoap.org/claims/EmailAddress|  
|AD FS 1. *x* по электронной почте, имя участника-пользователя|http://schemas.xmlsoap.org/claims/UPN|  
|Общее имя|http://schemas.xmlsoap.org/claims/CommonName|  
|Группы|http://schemas.xmlsoap.org/claims/Group|  
  
Должно быть отправлено только одно утверждение идентификатор имени в соответствующем формате. Если это условие выполнено, множество других утверждений можно отправлять, с учетом ограничений, описанных в таблице.  
  
> [!NOTE]  
> AD FS 1. *x* службы федерации можно интерпретировать только входящие утверждения с типом, начинающиеся с \(URI\) универсальный код ресурса из http://schemas.xmlsoap.org/claims/.  
  
## <a name="see-also"></a>См. также:
[Руководство по разработке служб AD FS в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)
