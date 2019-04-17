---
title: "AD FS строки = входа"
description: "Вопросы и ответы для AD FS 2016"
author: billmath
ms.author: billmath
manager: femila
ms.date: 06/27/2017
ms.topic: article
ms.custom: it-pro
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 8b98cdc27c9bd01d9855e98965f59ebe5257ed5c
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="active-directory-federation-services-promptlogin-parameter-support"></a>Службы федерации Active Directory запрос = поддержки параметр входа в систему
Следующий документ описывает встроенная поддержка prompt = параметр входа в систему, доступные в AD FS.

## <a name="what-is-promptlogin"></a>Что такое запрос = входа?  

Некоторые приложения Office 365 (при включенном современных идентификации) отправить параметр входа = запрос к Azure AD в рамках все запросы проверки подлинности.  По умолчанию, Azure AD преобразует это в два параметра: <code><b>wauth</b>=urn:oasis:names:tc:SAML:1.0:am:password</code>, и <code><b>wfresh</b>=0</code>.

Это может вызвать проблемы с корпоративной интрасети и сценариев использования многофакторной идентификации, в которых требуется тип проверки подлинности, отличные от имени пользователя и пароля.  

AD FS в Windows Server 2012 R2 с накопительным пакетом обновления июля 2016 появился встроенная поддержка prompt = параметр входа в систему.  Это значит, теперь у вас есть возможность настроить Azure AD для отправки параметр-— службу AD FS в рамках Azure AD и запросы на проверку подлинности Office 365.

### <a name="ad-fs-versions-that-support-promptlogin"></a>AD FS версий, поддерживающих строки = входа
Ниже приведен список версий Служб федерации Active Directory, которые поддерживают параметр входа = запрос.

- Накопительный пакет обновления AD FS в Windows Server 2012 R2 с июль 2016 г.

- AD FS в Windows Server 2016

## <a name="how-do-to-configure-your-azure-ad-tenant-to-send-promptlogin-to-ad-fs"></a>Как сделать, чтобы настроить клиент Azure AD для отправки запроса = вход в службы AD FS

Модуль Azure AD для PowerShell используется для настройки параметра.

> [!NOTE]
> Возможность входа prompt = (включен в свойстве PromptLoginBehavior) в настоящее время доступна только в ["модуль Azure AD для Powershell версии 1.0'](https://connect.microsoft.com/site1164/Downloads/DownloadDetails.aspx?DownloadID=59185), в которой командлеты именами, включающими «Msol», например Set-MsolDomainFederationSettings.  Он в данный момент недоступен через "версии 2.0 Azure AD для PowerShell модуля, командлеты имеют имена, как «задать-AzureAD\ *».

Чтобы настроить строки = поведение входа, ниже синтаксис командлета:

Пример 1.
```powershell
    Set-MsolDomainFederationSettings –DomainName <your domain name> -PreferredAuthenticationProtocol <your current protocol setting> 
```

Пример 2.
```powershell
    Set-MsolDomainFederationSettings –DomainName <your domain name> -SupportsMfa <$True|$False>
```

Пример 3.
```powershell
    Set-MsolDomainFederationSettings –DomainName <your domain name> -PromptLoginBehavior <TranslateToFreshPasswordAuth|NativeSupport|Disabled>
```

 
 Значения свойств PreferredAuthenticationProtocol, SupportsMfa и PromptLoginBehavior можно найти, просмотрите выходные данные командлета: ![Get-MsolDomainFederationSettings](media/AD-FS-Prompt-Login/GetMsol.png)
```powershell
    Get-MsolDomainFederationSettings -DomainName <your_domain_name> | fl *
 ```
> [!NOTE]
> По умолчанию, при выполнении Get-MsolDomainFederationSettings некоторые свойства не отображаются в консоли.  Чтобы просмотреть эти параметры, рекомендуется использовать | fl * для принудительного вывода всех свойств объекта.


Ниже приведены дополнительные сведения о параметр PromptLoginBehavior и его параметры.
   
   - <b>TranslateToFreshPasswordAuth</b> отправки поведение по умолчанию Azure AD означает <b>wauth</b> и <b>wfresh</b> для Служб федерации Active Directory вместо строки = входа
   - <b>NativeSupport</b> означает, что параметр входа в систему запрос = будут отправляться как для Служб федерации Active Directory
   - <b>Отключено</b> означает ничего не будет отправляться AD FS

