---
ms.assetid: ''
title: Политики управления доступом в AD FS
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: cc91cd9a446c8ca30471b65374ca99a7bd49d369
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59882375"
---
# <a name="controlling-access-to-organizational-data-with-active-directory-federation-services"></a>Управление доступом к данным организации с помощью служб федерации Active Directory

В этом документе содержится обзор управления доступом с AD FS по в локальной среде, гибридных и облачных сценариев.  

## <a name="ad-fs-and-conditional-access-to-on-premises-resources"></a>AD FS и условный доступ к локальным ресурсам 
С появлением служб федерации Active Directory были доступны для разрешения и ограничения доступа пользователей к ресурсам, исходя из атрибутов запроса и ресурс политики авторизации.  Как AD FS были перемещены в разных версиях, реализация этих политик было изменено.  Подробные сведения о возможностях управления доступом по версии см. в разделе:
- [Политики управления доступом в AD FS в Windows Server 2016](Access-Control-Policies-in-AD-FS.md)
- [Управление доступом в AD FS в Windows Server 2012 R2](Manage-Risk-with-Conditional-Access-Control.md)


## <a name="ad-fs-and-conditional-access-in-a-hybrid-organization"></a>AD FS и условного доступа в гибридной организации  

AD FS предоставляет компонент в локальной среде политики условного доступа в гибридном сценарии. Правила авторизации AD FS на основе следует использовать для ресурсов, отличных от Azure AD, такие как в локальной среде приложений непосредственно федерацию AD FS.  Компонент облачной обеспечивается [условного доступа Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access).  Azure AD Connect предоставляет плоскостью управления, их соединения.

Например при регистрации устройств в Azure AD для условного доступа к облачным ресурсам, устройства Azure AD Connect записи обратно возможности доступны сведения о регистрации устройства в локальной среде для использования и принудительное применение политик AD FS.  Таким образом, у вас есть согласованный подход к политики контроля доступа для обоих на локальном компьютере и к облачным ресурсам.  

![Условный доступ](../deployment/media/Plan-Device-based-Conditional-Access-on-Premises/ADFS_ITPRO4.png)  


### <a name="the-evolution-of-client-access-policies-for-office-365"></a>Эволюция политики клиентского доступа для Office 365
Многие из вас при использовании политики клиентского доступа с AD FS, чтобы ограничить доступ к Office 365 и другим службам Microsoft Online, на основе факторов, таких как местоположение клиента и тип используемого приложения клиента.  
- [Политики клиентского доступа в Windows Server 2012 R2 AD FS](Access-Control-Policies-W2K12.md)
- [Политики клиентского доступа в AD FS 2.0](Access-Control-Policies-in-AD-FS-2.md)

Некоторые примеры этих политик.
- Блокировка экстрасети клиентского доступа к Office 365
- Блокировка экстрасети клиентского доступа к Office 365, за исключением устройств, доступ к Exchange Online для Exchange Active Sync

Часто базовой за эти политики необходим для снижения риска утечки данных, гарантируя только авторизованные клиенты, приложения, которые не кэшируют данные, или устройств, которые можно отключить удаленно можно получить доступ к ресурсам.

Хотя выше документированные политики для служб AD FS работают в определенных сценариях описано, они имеют ограничения, поскольку они зависят от клиента не постоянно доступные данные.  Например в удостоверение клиентского приложения, только было доступно для Exchange Online на основе служб, а не для ресурсов, таких как SharePoint Online, где и тех же данных может осуществляться через браузер или толстого клиента, например Word или Excel.  Также службы федерации Active Directory не знает ресурса в Office 365, доступ к, таких как SharePoint Online или Exchange Online.

Чтобы устранить эти ограничения и обеспечить более надежным способом использовать политики для управления доступом к бизнес-данным в Office 365 или другим ресурсам на основе Azure AD, корпорация Microsoft представила условного доступа Azure AD.  Политики Azure AD условного доступа можно настроить для определенного ресурса, или для любого или всех ресурсов в Office 365, SaaS или пользовательские приложения в Azure AD.  Эти политики сводки по доверия устройства, расположения и других факторов.

Чтобы узнать больше о условного доступа Azure AD, см. в разделе [условного доступа в Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)

Изменение ключа реализации этих сценариев [современную проверку подлинности](https://blogs.office.com/2015/11/19/updated-office-365-modern-authentication-public-preview/), новый способ проверки подлинности пользователей и устройств, который работает так же, как у клиентов Office, Скайп, Outlook и браузеры.

## <a name="next-steps"></a>Следующие шаги
Дополнительные сведения об управлении доступом в облаке и в локальной среде см. в разделе:

- [Условный доступ в Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
- [Политики управления доступом в AD FS 2016](Access-Control-Policies-in-AD-FS.md)
