---
ms.assetid: 
title: "Политики управления доступом в AD FS"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 5e1e1b907e6fccbf2b9906106d3360bd9a6fd69d
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="controlling-access-to-organizational-data-with-active-directory-federation-services"></a>Управление доступом для данных организации с помощью служб федерации Active Directory

В этом документе представлен обзор управления доступом в AD FS в локальной среде, сценарии гибридного и в облаке.  

## <a name="ad-fs-and-conditional-access-to-on-premises-resources"></a>Условный доступ на локальных ресурсов и AD FS 
С момента внедрения служб федерации Active Directory политики авторизации были доступны ограничить или предоставления пользователям доступа к ресурсам на основе атрибутов запроса и ресурса.  Как службы федерации Active Directory была перемещена до версии, реализации этих политик было изменено.  Дополнительные сведения о функции управления доступом по версии см.:
- [Политики управления доступом в AD FS в Windows Server 2016](Access-Control-Policies-in-AD-FS.md)
- [Управление доступом в AD FS в Windows Server 2012 R2](Manage-Risk-with-Conditional-Access-Control.md)


## <a name="ad-fs-and-conditional-access-in-a-hybrid-organization"></a>Условный доступ в организации гибридного и AD FS  

AD FS обеспечивает компонент на локальные политики условного доступа в гибридном сценарии. Правила авторизации AD FS на основе следует использовать для ресурсов, отличных от Azure AD, такие как на локальном компьютере федеративных приложений непосредственно в AD FS.  Предоставленные облачным компонентом [Azure условным доступом в AD](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-conditional-access).  Azure AD Connect предоставляет подключение двух плоскости управления.

Например при регистрации устройства с Azure AD для условного доступа к облачным ресурсам, Azure AD Connect устройство записи обратно возможность обеспечивает сведения о регистрации устройств доступны на локальном компьютере для политик AD FS для использования и применения.  Таким образом, у вас есть согласованный способ доступа к политики управления на локальных и облачных ресурсов в.  

![условный доступ](../deployment/media/Plan-Device-based-Conditional-Access-on-Premises/ADFS_ITPRO4.png)  


### <a name="the-evolution-of-client-access-policies-for-office-365"></a>Следующий этап развития политик доступа клиента для Office 365
Многие из вас используете политик доступа клиента с AD FS для ограничения доступа к Office 365 и другие службы Microsoft Online, основаны на таких факторах, такие как расположение клиента и тип используемого приложения клиента.  
- [Политики доступа клиента в Windows Server 2012 R2 AD FS](Access-Control-Policies-W2K12.md)
- [Политики доступа клиента в AD FS 2.0](Access-Control-Policies-in-AD-FS-2.md)

Некоторые примеры этих политик.
- Блокировать все экстрасети клиентского доступа к Office 365
- Блокировать все экстрасети клиентского доступа к Office 365, за исключением устройств, доступа к Exchange Online для Exchange Active Sync

Часто является основной необходимость за эти политики для снижения риска утечки данных, обеспечивая только авторизованным клиентам, приложения, не кэшируют данные, или устройства, которые могут быть отключены удаленно можно получить доступ к ресурсам.

Хотя выше документально политики для служб AD FS работают в конкретных задокументированных сценариев, поскольку они зависят от данных клиента, не постоянный доступ имеют ограничения.  Например удостоверение клиентского приложения только предоставлялась для Exchange Online на основе служб, а не для ресурсы, такие как SharePoint Online, где может получать доступ к тем же данным через браузер или толстого клиента, например Word или Excel.  Также AD FS остается незамеченным ресурса в Office 365, которой осуществляется доступ, такие как SharePoint Online и Exchange Online.

Чтобы устранить эти ограничения и обеспечить более надежным способом, используйте политики для управления доступом к бизнес-данным в Office 365 или другие ресурсы на основе Azure AD, корпорация Майкрософт представила Azure условным доступом в AD.  Можно настроить политики Azure AD условного доступа, для определенного ресурса или для конкретной или всех ресурсов в Office 365, SaaS или пользовательских приложений в Azure AD.  Эти политики "Сводка" на устройство доверия, расположение и других факторов.

Чтобы узнать больше о Azure условным доступом в AD, см. [условного доступа в Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-conditional-access)

Включение этих сценариев изменение ключа [современных проверки подлинности](https://blogs.office.com/2015/11/19/updated-office-365-modern-authentication-public-preview/), новый способ проверки подлинности пользователей и устройств, которая работает одинаково во всех клиентов Office, Скайп, Outlook и браузеров.

## <a name="next-steps"></a>Дальнейшие действия
Дополнительные сведения о контроля доступа в облаке и локальной среде см.:

- [Условный доступ в Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-conditional-access)
- [Политики управления доступом в AD FS 2016](Access-Control-Policies-in-AD-FS.md)
