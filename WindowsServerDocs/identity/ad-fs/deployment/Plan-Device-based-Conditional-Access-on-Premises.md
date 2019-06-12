---
ms.assetid: c5eb3fa0-550c-4a2f-a0bc-698b690c4199
title: Планирование локального условного доступа на основе устройств
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 3a78334f64d9e51515757b01f2d788bf87f67a35
ms.sourcegitcommit: cd12ace92e7251daaa4e9fabf1d8418632879d38
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2019
ms.locfileid: "66501609"
---
# <a name="plan-device-based-conditional-access-on-premises"></a>Планирование локального условного доступа на основе устройств


В этом документе описываются политики условного доступа на основе устройств в гибридном сценарии, где локальных каталогов к Azure AD с помощью Azure AD Connect.     

## <a name="ad-fs-and-hybrid-conditional-access"></a>AD FS и гибридные условного доступа  

AD FS предоставляет компонент в локальной среде политик условного доступа в гибридном сценарии.  При регистрации устройств в Azure AD для условного доступа к облачным ресурсам, Azure AD Connect устройство записи обратно возможности доступны сведения о регистрации устройства в локальной среде для использования и принудительное применение политик AD FS.  Таким образом, у вас есть согласованный подход к политики контроля доступа для обоих на локальном компьютере и к облачным ресурсам.  

![Условный доступ](media/Plan-Device-based-Conditional-Access-on-Premises/ADFS_ITPRO4.png)  

### <a name="types-of-registered-devices"></a>Типы зарегистрированных устройств  
Существует три вида зарегистрированных устройств, которые отображаются в виде объектов устройств в Azure AD и может использоваться для условного доступа с помощью AD FS в локальной среде также.  

| |Добавить работу или учебной учетной записи  |Присоединение к Azure AD  |Windows 10 домену    
| --- | --- |--- | --- |
|Описание    |  Пользователям добавить свою работу или рабочую учетную запись для устройства BYOD в интерактивном режиме.  **Примечание.** Добавление рабочей или учебной учетной записи является заменой для присоединения к рабочему месту в Windows 8 и 8.1       | Пользователи присоединения устройства работы Windows 10 к Azure AD.|С помощью Azure AD автоматической регистрации присоединенных к домену устройств Windows 10.|           
|Как пользователи входят в устройства     |  Без имени входа для Windows в качестве рабочей или учебной учетной записи.  Вход с использованием учетной записи Майкрософт.       |   Имя входа для Windows в качестве учетной записи (рабочую или учебную), регистрации устройства.      |     Вход с использованием учетной записи AD.|      
|Управление устройствами    |      Политики управления мобильными Устройствами (с помощью дополнительных регистрации в Intune)   | Политики управления мобильными Устройствами (с помощью дополнительных регистрации в Intune)        |   Групповая политика, System Center Configuration Manager (SCCM) |
|Тип доверия AD Azure|К рабочему месту|Присоединенные к Azure AD|Присоединен к домену  |     
|Расположение параметров W10    | Параметры > учетные записи > учетной записи > Добавить рабочую или учебную учетную запись        | Параметры > Система > о > присоединение к Azure AD       |   Параметры > Система > о > присоединение к домену |       
|Также доступно для устройств iOS и Android?   |    Да     |       Нет  |   Нет   |   

  

Дополнительные сведения о различных способах регистрации устройств см. также:  
* [Использование устройств Windows 10 в вашей рабочей области](https://azure.microsoft.com/documentation/articles/active-directory-azureadjoin-windows10-devices/)  
* [Настройка устройств Windows 10 для работы](https://jairocadena.com/2016/01/18/setting-up-windows-10-devices-for-work-domain-join-azure-ad-join-and-add-work-or-school-account/)  
[Присоединение к Azure Active Directory для Windows 10 Mobile](https://technet.microsoft.com/itpro/windows/manage/join-windows-10-mobile-to-azure-active-directory)  

### <a name="how-windows-10-user-and-device-sign-on-is-different-from-previous-versions"></a>Как пользователь Windows 10 и устройства входа отличается от предыдущих версий  
Для Windows 10 и AD FS 2016, существуют некоторые новые компоненты проверки подлинности и регистрации устройств следует знать о (особенно если вы уже знакомы, с помощью регистрации устройств и «присоединение к рабочему месту» в предыдущих выпусках).  

Во-первых, в Windows 10 и AD FS в Windows Server 2016, регистрация устройств и проверки подлинности больше не основывается исключительно на x X509 сертификат пользователя.  Нет новых и более надежный протокол, который обеспечивает более высокий уровень безопасности и более удобную работу пользователя.  Ключевыми отличиями являются, что для присоединения к домену Windows 10 и присоединения к Azure AD, имеется x X509 сертификат компьютера и новые учетные данные, называемых PRT.  Вы можете ознакомиться с ними [здесь](https://jairocadena.com/2016/01/18/how-domain-join-is-different-in-windows-10-with-azure-ad/) и [здесь](https://jairocadena.com/2016/02/01/azure-ad-join-what-happens-behind-the-scenes/).  

Во-вторых, Windows 10 и AD FS 2016 поддерживают проверку подлинности пользователя, с помощью Microsoft Passport for Work, который вы можете читать о [здесь](https://jairocadena.com/2016/03/09/azure-ad-and-microsoft-passport-for-work-in-windows-10/) и [здесь](https://azure.microsoft.com/documentation/articles/active-directory-azureadjoin-passport-deployment/).  

AD FS 2016 предоставляет простой устройств и пользователей на основе PRT и Passport учетных данных единого входа.  В этом документе, выполнив действия, можно включить эти возможности и см. в разделе, их работы.  

### <a name="device-access-control-policies"></a>Политики управления доступом устройств  
Можно ли использовать устройства в простые правила управления доступом в AD FS такие как:  

- Разрешить доступ только с зарегистрированным устройством   
- Требовать многофакторной проверки подлинности, если устройство не зарегистрировано  

Эти правила можно объединить с других факторов, таких как доступ сетевого расположения и многофакторной проверки подлинности, создание политики условного доступа на широкие возможности, такие как:  


- Требуйте многофакторной проверки подлинности для незарегистрированных устройств, доступ к из вне корпоративной сети, за исключением членами определенной группы или группы  

С помощью AD FS 2016, специально для того, чтобы требовать уровень доверия для конкретного устройства также можно настроить эти политики: либо **проверку подлинности**, **управляемых**, или **соответствует**.  

Дополнительные сведения о настройке AD FS политики контроля доступа, см. в разделе [политики управления доступом в AD FS](../../ad-fs/operations/Access-Control-Policies-in-AD-FS.md).  

#### <a name="authenticated-devices"></a>Прошедшие проверку подлинности устройств  
Прошедшие проверку подлинности устройства, зарегистрированные устройства, не зарегистрированных в MDM (Intune и сторонним поставщиком MDMs для Windows 10, Intune только для iOS и Android).   

Прошедшие проверку подлинности устройства имеют **isManaged** AD FS утверждение со значением **FALSE**. (В то время как устройств, которые не зарегистрированы вообще имеют этого утверждения.)  Прошедшие проверку подлинности устройств (и все зарегистрированные устройства), получат isKnown AD FS утверждение со значением **TRUE**.  

#### <a name="managed-devices"></a>Управляемые устройства:   

Управляемые устройства находятся зарегистрированных устройств, зарегистрированных в MDM.  

Управляемые устройства имеют isManaged AD FS утверждение со значением **TRUE**.  

#### <a name="devices-compliant-with-mdm-or-group-policies"></a>Устройств, соответствующих (управления мобильными Устройствами или групповые политики)  
Совместимые устройства, зарегистрированные устройства, не только зарегистрированных в MDM, кроме политикам управления мобильными Устройствами. (Сведения о соответствии происходит с помощью MDM и записывается в Azure AD).  

Соответствующие требованиям устройства будут иметь **isCompliant** AD FS утверждение со значением **TRUE**.    

Полный список устройств AD FS 2016 и утверждения условного доступа, см. в разделе [ссылку](#reference).  


## <a name="reference"></a>Ссылка  
#### <a name="complete-list-of-new-ad-fs-2016-and-device-claims"></a>Полный список новых AD FS 2016 и заявки на доступ  

* https://schemas.microsoft.com/ws/2014/01/identity/claims/anchorclaimtype  
* http://schemas.xmlsoap.org/ws/2005/05/identity/claims/implicitupn  
* https://schemas.microsoft.com/2014/03/psso  
* https://schemas.microsoft.com/2015/09/prt  
* http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn  
* https://schemas.microsoft.com/ws/2008/06/identity/claims/primarygroupsid  
* https://schemas.microsoft.com/ws/2008/06/identity/claims/primarysid  
* http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name  
* https://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname  
* https://schemas.microsoft.com/ws/2008/06/identity/claims/groupsid  
* https://schemas.microsoft.com/2012/01/devicecontext/claims/registrationid  
* https://schemas.microsoft.com/2012/01/devicecontext/claims/displayname  
* https://schemas.microsoft.com/2012/01/devicecontext/claims/identifier  
* https://schemas.microsoft.com/2012/01/devicecontext/claims/ostype  
* https://schemas.microsoft.com/2012/01/devicecontext/claims/osversion  
* https://schemas.microsoft.com/2012/01/devicecontext/claims/ismanaged  
* https://schemas.microsoft.com/2012/01/devicecontext/claims/isregistereduser  
* https://schemas.microsoft.com/2014/02/devicecontext/claims/isknown  
* https://schemas.microsoft.com/2014/02/deviceusagetime  
* https://schemas.microsoft.com/2014/09/devicecontext/claims/iscompliant  
* https://schemas.microsoft.com/2014/09/devicecontext/claims/trusttype  
* https://schemas.microsoft.com/claims/authnmethodsreferences  
* https://schemas.microsoft.com/2012/01/requestcontext/claims/x-ms-client-user-agent  
* https://schemas.microsoft.com/2012/01/requestcontext/claims/x-ms-endpoint-absolute-path  
* https://schemas.microsoft.com/ws/2012/01/insidecorporatenetwork  
* https://schemas.microsoft.com/2012/01/requestcontext/claims/client-request-id  
* https://schemas.microsoft.com/2012/01/requestcontext/claims/relyingpartytrustid  
* https://schemas.microsoft.com/2012/01/requestcontext/claims/x-ms-client-ip  
* https://schemas.microsoft.com/2014/09/requestcontext/claims/userip  
* https://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod  
