---
ms.assetid: 04b63d9f-e924-4146-9b1d-785ed8b4239c
title: Планирование взаимодействия со службами федерации Active Directory 1.x
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: e9f72bd83c90a804749329521a72e3232589c735
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71407960"
---
# <a name="planning-for-interoperability-with-ad-fs-1x"></a>Планирование взаимодействия со службами федерации Active Directory 1.x

Службы федерации Active Directory (AD FS) \(AD FS @ no__t-1 серверы федерации под управлением Windows Server® 2012 могут взаимодействовать с AD FS 1,0 \(installed с Windows Server 2003 R2 @ no__t-3 служба федерации и AD FS 1,1 \(installed с Windows Server 2008 или Windows Server 2008 R2 @ no__t-5 служба федерации. Поддерживаются любые из указанных ниже сочетаний.  

-   Любой AD FS 1. *x* служба федерации может отправить утверждение, которое может использоваться AD FS Служба федерации в Windows Server 2012. Дополнительные сведения см. в разделе [Checklist: Настройка AD FS на использование утверждений от AD FS 1. x @ no__t-0.  

-   Любой AD FS служба федерации в Windows Server 2012 может отправить AD FS 1. утверждение *x*\-compatible, которое может быть использовано AD FS 1. *x* служба Федерации. Дополнительные сведения см. в разделе [Checklist: Настройка AD FS для отправки утверждений в AD FS 1. x служба федерации @ no__t-0.  

-   Любой AD FS служба федерации в Windows Server 2012 может отправить AD FS 1. утверждение *x*\-compatible, которое может быть использовано одним или несколькими веб-серверами, на которых работает AD FS 1. *x* Claims @ no__t-3aware Web Agent. Дополнительные сведения см. в разделе [Checklist: Настройка AD FS для отправки утверждений в веб-агент AD FS 1. x с поддержкой утверждений @ no__t-0.  

> [!NOTE]  
> AD FS не поддерживает и не взаимодействуют с AD FS 1. Веб-агент *x* Windows NT на основе маркеров.  

AD FS 1. утверждение *x*\-compatible — утверждение, которое может быть отправлено AD FSом служба Федерации в Windows Server 2012 и понятным AD FS 1. *x* служба Федерации. Чтобы AD FS 1. *x* служба федерации может использовать утверждения, которые отправляет AD FS Служба федерации, должен быть отправлен идентификатор имени \(ID @ no__t-2.  

## <a name="understanding-the-name-id-claim-type"></a>Сведения о типе утверждений "Идентификатор имени"  
Тип утверждений "Идентификатор имени" аналогичен типу утверждений удостоверений, который используется в AD FS 1.*x* . Его необходимо использовать при любом взаимодействии с AD FS 1.*x*. Тип утверждения идентификатора имени включает либо AD FS 1. *x* служба федерации или AD FS 1. *x* Claims @ no__t-2aware Web Agent для использования утверждений, которые AD FS в Windows Server 2012, при условии, что эти утверждения отправляются в одном из форматов идентификаторов имен, указанных в следующей таблице.  


|      Формат идентификатора имени       |               Соответствующий код URI                |
|---------------------------|------------------------------------------------|
| Адрес электронной почты AD FS 1.*x* | http://schemas.xmlsoap.org/claims/EmailAddress |
|   Имя участника-пользователя электронной почты AD FS 1.*x*   |     http://schemas.xmlsoap.org/claims/UPN      |
|        Общее имя        |  http://schemas.xmlsoap.org/claims/CommonName  |
|           Группа           |    http://schemas.xmlsoap.org/claims/Group     |

Должно быть отправлено только одно утверждение типа "Идентификатор имени" в соответствующем формате. Если это условие выполнено, можно отправлять множество других утверждений с учетом ограничений, описанных в таблице.  

> [!NOTE]  
> AD FS 1. *x* служба федерации может интерпретировать только типы входящих утверждений, которые начинаются с универсального идентификатора ресурса \(URI @ no__t-2 из http://schemas.xmlsoap.org/claims/.  

## <a name="see-also"></a>См. также
[Руководство по разработке служб федерации Active Directory в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)
