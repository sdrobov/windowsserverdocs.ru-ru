---
title: AD FS Prompt = имя входа
description: Часто задаваемые вопросы по AD FS 2016
author: billmath
ms.author: billmath
manager: femila
ms.date: 06/27/2017
ms.topic: article
ms.custom: it-pro
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: a80678f5d2773e3fcd7a95032853249dc36d5616
ms.sourcegitcommit: 2a15de216edde8b8e240a4aa679dc6d470e4159e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2020
ms.locfileid: "77465528"
---
# <a name="active-directory-federation-services-promptlogin-parameter-support"></a>службы федерации Active Directory (AD FS) Prompt = поддержка параметров входа

В следующем документе описывается собственная поддержка параметра Prompt = Login, доступного в AD FS.

## <a name="what-is-promptlogin"></a>Что такое Prompt = имя входа?

Когда приложения должны запрашивать новую проверку подлинности из Azure AD, то есть для повторной проверки подлинности пользователя в Azure AD необходимо, чтобы он был `prompt=login` отправлен в Azure AD в рамках запроса на проверку подлинности.

Если этот запрос предназначен для федеративного пользователя, Azure AD необходимо сообщить IdP, например AD FS, что запрос предназначен для новой проверки подлинности.

По умолчанию Azure AD преобразует `prompt=login` в `wfresh=0` и `wauth=https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/password` при отправке запросов на проверку подлинности в федеративный IdP.

Эти параметры означают следующее:

- `wfresh=0`: выполнять новую проверку подлинности
- `wauth=https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/password`: используйте имя пользователя и пароль для нового запроса проверки подлинности

Это может вызвать проблемы с корпоративными интрасетями и сценариями многофакторной проверки подлинности, в которых требуется тип проверки подлинности, отличный от имени пользователя и пароля, запрошенного параметром `wauth`.  

AD FS в Windows Server 2012 R2 с накопительным пакетом обновления за Июль 2016 представил встроенную поддержку параметра `prompt=login`. Это означает, что теперь Azure AD может отправить этот параметр "как есть" в AD FS службу как часть запросов проверки подлинности Azure AD и Office 365.

## <a name="ad-fs-versions-that-support-promptlogin"></a>AD FS версии, поддерживающие Prompt = имя входа

Ниже приведен список версий AD FS, которые поддерживают параметр `prompt=login`.

- AD FS в Windows Server 2012 R2 с накопительным пакетом обновления за Июль 2016
- AD FS в Windows Server 2016

## <a name="how-to-configure-a-federated-domain-to-send-promptlogin-to-ad-fs"></a>Настройка федеративного домена для отправки запроса = вход в AD FS

Для настройки параметра используйте модуль Azure AD PowerShell.

> [!NOTE]
> Функция `prompt=login` (включенная свойством `PromptLoginBehavior`) в настоящее время доступна только в [модуле Azure AD PowerShell версии 1,0](https://connect.microsoft.com/site1164/Downloads/DownloadDetails.aspx?DownloadID=59185), в котором командлеты имеют имена, включающие "MSOL", например Set-MsolDomainFederationSettings.  В настоящее время он недоступен через версию 2,0 модуля Azure AD PowerShell, у командлетов которых есть такие имена, как Set-AzureAD\*.

1. Сначала получите текущие значения `PreferredAuthenticationProtocol`, `SupportsMfa`и `PromptLoginBehavior` для федеративного домена, выполнив следующую команду PowerShell:

```powershell
    Get-MsolDomainFederationSettings -DomainName <your_domain_name> | Format-List *
```

> [!NOTE]
> Выходные данные `Get-MsolDomainFederationSettings` по умолчанию не отображают определенные свойства в консоли. Чтобы просмотреть все свойства, необходимо передать его выходные данные по конвейеру (`|`), чтобы получить `Format-List *` для принудительного вывода всех свойств объекта.

![Get-MsolDomainFederationSettings](media/AD-FS-Prompt-Login/GetMsol.png)

> [!NOTE]
> Если значение свойства `PromptLoginBehavior` является пустым (`$null`), используется поведение `TranslateToFreshPasswordAuth`.

2. Настройте нужное значение `PromptLoginBehavior`, выполнив следующую команду:

```powershell
    Set-MsolDomainFederationSettings –DomainName <your_domain_name> -PreferredAuthenticationProtocol <current_value_from_step1> -SupportsMfa <current_value_from_step1> -PromptLoginBehavior <TranslateToFreshPasswordAuth|NativeSupport|Disabled>
```

Ниже приведены возможные значения параметра `PromptLoginBehavior` и их значение.

- **Транслатетофрешпассвордаус**: означает поведение Azure AD по умолчанию для перевода `prompt=login` `wauth=https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/password` и `wfresh=0`.
- **Нативесуппорт**: означает, что параметр `prompt=login` будет отправляться как AD FS. Это рекомендуемое значение, если AD FS находится в Windows Server 2012 R2 с накопительным пакетом обновления за Июль 2016 или более поздней версии.
- **Disabled (отключено**) означает, что в AD FS отправляются только `wfresh=0`.
