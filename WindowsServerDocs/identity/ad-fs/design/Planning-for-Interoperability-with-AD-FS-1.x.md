---
ms.assetid: 04b63d9f-e924-4146-9b1d-785ed8b4239c
title: Планирование взаимодействия со службами федерации Active Directory 1.x
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 9c5f49bd0ee0da9c3b92bad96f16ca310f82c239
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66445329"
---
# <a name="planning-for-interoperability-with-ad-fs-1x"></a>Планирование взаимодействия со службами федерации Active Directory 1.x

Службы федерации Active Directory \(AD FS\) серверами федерации под управлением Windows Server® 2012, совместимы с обоих AD FS 1.0 \(устанавливается вместе с Windows Server 2003 R2\) и службами федерации AD FS 1.1 \(устанавливается вместе с Windows Server 2008 или Windows Server 2008 R2\) службы федерации. Поддерживаются любые из указанных ниже сочетаний.  

-   Любой AD FS 1. *x* служба федерации может отправлять утверждения, которые могут использоваться службой федерации AD FS в Windows Server 2012. Дополнительные сведения см. в разделе [контрольный список: Настройка AD FS использовать утверждения из AD FS 1.x](../../ad-fs/deployment/Checklist--Configuring-AD-FS--to-Consume-Claims-from-AD-FS-1.x.md).  

-   Любой службой федерации AD FS в Windows Server 2012 можно отправлять с AD FS 1. *x*\-утверждения, совместимые, которые могут использоваться службой AD FS 1. *x* службы федерации. Дополнительные сведения см. в разделе [контрольный список: Настройка служб AD FS для отправки утверждений в службе федерации AD FS 1.x](../../ad-fs/deployment/Checklist--Configuring-AD-FS-to-Send-Claims-to-an-AD-FS-1.x-Federation-Service.md).  

-   Любой службой федерации AD FS в Windows Server 2012 можно отправлять с AD FS 1. *x*\-утверждения, совместимые, который можно использовать один или несколько веб-серверами AD FS 1. *x* утверждений\-виду веб-агент. Дополнительные сведения см. в разделе [контрольный список: Настройка служб AD FS для отправки утверждений для агента AD FS 1.x Claims-Aware Web](../../ad-fs/deployment/Checklist--Configuring-AD-FS-to-Send-Claims-to-an-AD-FS-1.x-Claims-Aware-Web-Agent.md).  

> [!NOTE]  
> Службы федерации Active Directory не поддерживает или взаимодействии с AD FS 1. *x* токены веб-агент Windows NT.  

AD FS 1. *x*\-утверждения, совместимые является утверждением, которая может быть отправлено службой федерации AD FS в Windows Server 2012 и понятны AD FS 1. *x* службы федерации. Таким образом, AD FS 1. *x* службы федерации могла принимать утверждения, отправляемые службой федерации AD FS, идентификатор имени \(идентификатор\) утверждения типа должны быть отправлены.  

## <a name="understanding-the-name-id-claim-type"></a>Сведения о типе утверждений "Идентификатор имени"  
Тип утверждений "Идентификатор имени" аналогичен типу утверждений удостоверений, который используется в AD FS 1.*x* . Его необходимо использовать при любом взаимодействии с AD FS 1.*x*. Утверждения идентификатора имени типа включает либо AD FS 1. *x* службы федерации или AD FS 1. *x* утверждений\-виду веб-агента для использования утверждения, отправляемые AD FS в Windows Server 2012, до тех пор, пока эти утверждения отправляются в одном из форматов в следующей таблице.  


|      Формат идентификатора имени       |               Соответствующий код URI                |
|---------------------------|------------------------------------------------|
| Адрес электронной почты AD FS 1.*x* | http://schemas.xmlsoap.org/claims/EmailAddress |
|   Имя участника-пользователя электронной почты AD FS 1.*x*   |     http://schemas.xmlsoap.org/claims/UPN      |
|        Общее имя        |  http://schemas.xmlsoap.org/claims/CommonName  |
|           Группа           |    http://schemas.xmlsoap.org/claims/Group     |

Должно быть отправлено только одно утверждение типа "Идентификатор имени" в соответствующем формате. Если это условие выполнено, можно отправлять множество других утверждений с учетом ограничений, описанных в таблице.  

> [!NOTE]  
> AD FS 1. *x* служба федерации может интерпретировать только за входящими утверждениями, которые начинаются с Uniform Resource Identifier \(URI\) из http://schemas.xmlsoap.org/claims/.  

## <a name="see-also"></a>См. также
[Руководство по разработке служб федерации Active Directory в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)
