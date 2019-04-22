---
title: AD FS строки = имя входа
description: Часто задаваемые вопросы для AD FS 2016
author: billmath
ms.author: billmath
manager: femila
ms.date: 06/27/2017
ms.topic: article
ms.custom: it-pro
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 6a4b6cfe98064181824e210be9031a0f67cb4b75
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59824635"
---
# <a name="active-directory-federation-services-promptlogin-parameter-support"></a>Запрос служб федерации Active Directory = параметр поддержки входа в систему
В следующем документе описано встроенную поддержку параметр prompt = имя входа, доступные в AD FS.

## <a name="what-is-promptlogin"></a>Что такое prompt = login?  

Некоторые приложения Office 365 (с поддержкой современной аутентификацией) отправки параметр prompt = имя входа в Azure AD как часть все запросы проверки подлинности.  По умолчанию Azure AD преобразует это в два параметра: <code> <b> wauth </b> =urn:oasis:names:tc:SAML:1.0:am:password </code>, и <code> <b> wfresh </b> =0 </code> .

Это может вызвать проблемы с корпоративной интрасети и сценарии многофакторной проверки подлинности, в которых требуется тип проверки подлинности, отличный от имени пользователя и пароля.  

AD FS в Windows Server 2012 R2 с накопительным пакетом обновления за июль 2016 появилась встроенная поддержка параметр prompt = login.  Это означает, что теперь у вас есть возможность настроить Azure AD для отправки этот параметр в виде-— для службы AD FS, как часть Azure AD и запросы проверки подлинности Office 365.

### <a name="ad-fs-versions-that-support-promptlogin"></a>Версии AD FS, которые поддерживают строки = имя входа
Ниже приведен список версий AD FS, которые поддерживают параметр prompt = login.

- Накопительный пакет обновления AD FS в Windows Server 2012 R2 с июля 2016 г.

- AD FS в Windows Server 2016

## <a name="how-do-to-configure-your-azure-ad-tenant-to-send-promptlogin-to-ad-fs"></a>Инструкции для настройки вашего клиента Azure AD для отправки prompt = имя входа в службы AD FS

Настройка параметров, используйте модуль Azure AD PowerShell.

> [!NOTE]
> Возможность входа prompt = (включено по свойству PromptLoginBehavior) в настоящее время доступна только в ["модуля Azure AD Powershell версии 1.0''](https://connect.microsoft.com/site1164/Downloads/DownloadDetails.aspx?DownloadID=59185), в котором командлеты имеют имена, содержащие «Msol», такие как SET-MsolDomainFederationSettings.  Она недоступна в настоящее время с помощью "версии 2.0 Azure AD PowerShell модуля, командлеты имеют имена как «Set-AzureAD\*«.

Настроить запрос = имя входа поведение, в представленном ниже синтаксисе командлета:

Пример 1:
```powershell
    Set-MsolDomainFederationSettings –DomainName <your domain name> -PreferredAuthenticationProtocol <your current protocol setting> 
```

Пример 2:
```powershell
    Set-MsolDomainFederationSettings –DomainName <your domain name> -SupportsMfa <$True|$False>
```

Пример 3.
```powershell
    Set-MsolDomainFederationSettings –DomainName <your domain name> -PromptLoginBehavior <TranslateToFreshPasswordAuth|NativeSupport|Disabled>
```

 
 Значения свойств PreferredAuthenticationProtocol SupportsMfa и PromptLoginBehavior можно найти, просмотрев выходные данные командлета: ![Get-MsolDomainFederationSettings](media/AD-FS-Prompt-Login/GetMsol.png)
```powershell
    Get-MsolDomainFederationSettings -DomainName <your_domain_name> | fl *
 ```
> [!NOTE]
> По умолчанию, при выполнении командлета Get-MsolDomainFederationSettings некоторые свойства не отображаются в консоли.  Чтобы просмотреть эти параметры, рекомендуется использовать | fl * для принудительного вывода всех свойств объекта.


Ниже приведен Дополнительные сведения о параметре PromptLoginBehavior и его параметры.
   
   - <b>TranslateToFreshPasswordAuth</b> означает, что Azure AD по умолчанию отправка <b>wauth</b> и <b>wfresh</b> к AD FS вместо строки = имя входа
   - <b>NativeSupport</b> означает, что параметр prompt = login будут отправлены для AD FS
   - <b>Отключенные</b> означает, что ничего не будет отправляться AD FS

