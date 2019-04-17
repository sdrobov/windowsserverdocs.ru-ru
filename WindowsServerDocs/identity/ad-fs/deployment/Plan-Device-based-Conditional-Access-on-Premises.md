---
ms.assetid: c5eb3fa0-550c-4a2f-a0bc-698b690c4199
title: "Планирование условного доступа на основе устройства локально"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 6303bba92ce4f4f99ae8e5095060b06885e427d6
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="plan-device-based-conditional-access-on-premises"></a>Планирование условного доступа на основе устройства локально

>Область применения: Windows Server 2016

В этом документе описываются политики условного доступа на основе устройств в гибридном сценарии, в которых в локальный каталог подключены к Azure AD с помощью Azure AD Connect.     

## <a name="ad-fs-and-hybrid-conditional-access"></a>Службы федерации Active Directory и гибридные условного доступа  

AD FS обеспечивает компонент на локальных политик условного доступа в гибридном сценарии.  При регистрации устройства с Azure AD для условного доступа к облачным ресурсам, Azure AD Connect устройство записи обратно возможность обеспечивает сведения о регистрации устройств доступны на локальном компьютере для политик AD FS для использования и применения.  Таким образом, у вас есть согласованный способ доступа к политики управления на локальных и облачных ресурсов в.  

![условный доступ](media/Plan-Device-based-Conditional-Access-on-Premises/ADFS_ITPRO4.png)  

### <a name="types-of-registered-devices"></a>Типы зарегистрированных устройств  
Существует три типа зарегистрированных устройств, каждый из которых отображаются в виде объектов устройства в Azure AD и может использоваться для условного доступа с помощью Служб федерации Active Directory на локальном компьютере также.  

| |Добавьте рабочую или учебную учетную запись  |Присоединение к Azure AD  |Присоединение к Domian Windows 10    
| --- | --- |--- | --- |
|Описание    |  Пользователи добавить свою работу или учебной учетной записи устройства BYOD интерактивном режиме.  **Примечание:** добавлением рабочей или учебной учетной записи — это замена для присоединения к рабочему месту в Windows 8/8.1       | Пользователи свое устройство Windows 10 рабочих присоединение к Azure AD.|Присоединен к домену устройств с Windows 10 автоматически регистрируются в Azure AD.|           
|Как пользователи войти на устройство     |  Без входа в систему Windows с рабочей или учебной учетной записи.  Войдите в систему с учетной записью Майкрософт.       |   При входе в Windows (рабочей или учебной) учетных записей, зарегистрированные устройства.      |     Войдите, используя учетную запись AD.|      
|Управление устройствами    |      Политики MDM (Регистрация в решении дополнительных Intune)   | Политики MDM (Регистрация в решении дополнительных Intune)        |   Групповая политика, System Center Configuration Manager (SCCM) |
|Тип доверия AD с Azure|К рабочему месту|Присоединенные к Azure AD|Присоединен к домену  |     
|Расположение параметров W10    | Параметры > учетные записи > вашей учетной записи > Добавление рабочей или учебной учетной записи        | Параметры > Система > о > присоединения к Azure AD       |   Параметры > Система > о > присоединиться к домену |       
|Также доступны для устройств iOS и Android?   |    Да     |       Нет  |   Нет   |   

  

Дополнительные сведения о различных способах регистрации устройств см. также:  
* [С помощью устройств с Windows 10 на рабочем месте](https://azure.microsoft.com/en-us/documentation/articles/active-directory-azureadjoin-windows10-devices/)  
* [Настройка устройств для работы с Windows 10](https://jairocadena.com/2016/01/18/setting-up-windows-10-devices-for-work-domain-join-azure-ad-join-and-add-work-or-school-account/)  
[Присоединение Windows 10 Mobile к Azure Active Directory](https://technet.microsoft.com/itpro/windows/manage/join-windows-10-mobile-to-azure-active-directory)  

### <a name="how-windows-10-user-and-device-sign-on-is-different-from-previous-versions"></a>Как пользователь Windows 10 и входа устройства отличается от предыдущих версий  
Для Windows 10 и AD FS 2016 существуют некоторые аспекты регистрации устройства и проверки подлинности необходимо узнать, какие (особенно если вы хорошо знакомы регистрации устройств и «присоединение к рабочему месту» в предыдущих выпусках).  

Во-первых, в Windows 10 и AD FS в Windows Server 2016, регистрации устройства и проверки подлинности больше не основан исключительно на X509 сертификат пользователя.  Существует новый более надежное и протокол, который обеспечивает более высокий уровень безопасности и более удобную работу пользователей.  Основные различия, что, для присоединения к домену Windows 10 и присоединение к Azure AD, имеется X509 сертификата компьютера и новых учетных данных, называется PRT.  Вы можете прочитать все по этому [здесь](https://jairocadena.com/2016/01/18/how-domain-join-is-different-in-windows-10-with-azure-ad/) и [здесь](https://jairocadena.com/2016/02/01/azure-ad-join-what-happens-behind-the-scenes/).  

Во-вторых, Windows 10 и AD FS 2016 поддерживает проверку подлинности пользователя, с помощью Microsoft Passport для работы, которое вы можете прочитать о [здесь](https://jairocadena.com/2016/03/09/azure-ad-and-microsoft-passport-for-work-in-windows-10/) и [здесь](https://azure.microsoft.com/en-us/documentation/articles/active-directory-azureadjoin-passport-deployment/).  

AD FS 2016 предоставляет безупречное устройства и пользователя на основе PRT и Passport учетных данных единого входа.  Следуя инструкциям в этом документе, можно включить эти возможности и увидеть их работы.  

### <a name="device-access-control-policies"></a>Политики управления доступом для устройства  
Устройства можно использовать в простых правилами контроля доступа в AD FS таких как:  

- Разрешить доступ только с зарегистрированным устройством   
- требуется несколькими двухфакторной проверки подлинности, когда устройство не зарегистрировано  

Эти правила можно затем объединяется с других факторов, таких как доступ к сети и несколькими проверки подлинности, создание политики форматированного условного доступа, например:  


- требуется несколькими двухфакторной проверки подлинности для отменена регистрация устройств, доступ к корпоративной сети, за исключением члены определенной группы или групп  

С AD FS 2016, эти политики можно настроить специально для уровня доверия конкретного устройства также требуется: либо **с проверкой подлинности**, **управляемых**, или **соответствует**.  

Дополнительные сведения о настройке Служб федерации Active Directory политики контроля доступа см. в разделе [политики управления доступом в AD FS](../../ad-fs/operations/Access-Control-Policies-in-AD-FS.md).  

#### <a name="authenticated-devices"></a>С проверкой подлинности устройств  
С проверкой подлинности устройств, зарегистрированных устройств, которые не зарегистрирован в MDM (Intune и сторонние службы MDM для Windows 10, Intune только для устройств iOS и Android).   

С проверкой подлинности устройства имеют **isManaged** AD FS утверждение со значением **FALSE**. (В то время как устройства, которые не зарегистрированы вообще будет нехватки это утверждение.) С проверкой подлинности устройств (и всех зарегистрированных устройств), имеют isKnown AD FS утверждение со значением **TRUE**.  

#### <a name="managed-devices"></a>Управляемые устройства:   

Управляемые устройства, зарегистрированные устройства, зарегистрированные с помощью MDM.  

Управляемые устройства имеют isManaged AD FS утверждение со значением **TRUE**.  

#### <a name="devices-compliant-with-mdm-or-group-policies"></a>Устройства, которые соответствуют (MDM или групповой политики)  
Совместимые устройства, зарегистрированные устройства, которые не только зарегистрированы с помощью MDM, кроме соблюдение политик MDM. (Сведения о соответствии создается с помощью MDM и записывается в Azure AD).  

Совместимые устройства будет иметь **isCompliant** AD FS утверждение со значением **TRUE**.    

Полный список устройств AD FS 2016 и утверждений условным доступом в разделе [ссылки](#reference).  


## <a name="reference"></a>Справочник по  
#### <a name="complete-list-of-new-ad-fs-2016-and-device-claims"></a>Полный список новых AD FS 2016 и заявки на доступ  

* https://schemas.microsoft.com/ws/2014/01/identity/claims/anchorclaimtype  
* http://schemas.xmlsoap.org/ws/2005/05/IDENTITY/claims/implicitupn  
* https://schemas.microsoft.com/2014/03/psso  
* https://schemas.microsoft.com/2015/09/prt  
* http://schemas.xmlsoap.org/ws/2005/05/IDENTITY/claims/UPN  
* https://schemas.microsoft.com/ws/2008/06/identity/claims/primarygroupsid  
* https://schemas.microsoft.com/ws/2008/06/identity/claims/primarysid  
* http://schemas.xmlsoap.org/ws/2005/05/IDENTITY/claims/Name  
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
