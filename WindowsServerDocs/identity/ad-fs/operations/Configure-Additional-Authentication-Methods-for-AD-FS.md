---
ms.assetid: ddfbbda3-30ca-4537-af12-667efc6f63ff
title: Настройка дополнительных методов проверки подлинности для службы федерации Active Directory
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 10/04/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 88c4d976b9808d254dc1681ce9eee3ca556824ab
ms.sourcegitcommit: 0b5fd4dc4148b92480db04e4dc22e139dcff8582
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66189790"
---
# <a name="configure-additional-authentication-methods-for-ad-fs"></a>Настройка дополнительных методов проверки подлинности для службы федерации Active Directory

Для многофакторной проверки подлинности (MFA) необходимо выбрать по крайней мере один дополнительный метод проверки подлинности. По умолчанию в федерации служб Active Directory (AD FS) в Windows Server 2012 R2 для дополнительной проверки подлинности можно выбрать сертификат подлинности (другими словами, смарт карта).

> [!NOTE]
> Выбирая проверку подлинности сертификата, убедитесь в том, что сертификаты смарт-карт представлены в защищенном виде и имеют требование ввода ПИН-кода.

Знали ли вы, что Microsoft Azure предоставляет аналогичные функциональные возможности в облаке? Подробнее о [решениях для удостоверений Microsoft Azure](http://aka.ms/m2w274).<br /><br />Создайте гибридное решение для удостоверений в Microsoft Azure:<br /> - [Дополнительные сведения о многофакторная Идентификация Azure.](http://aka.ms/ey6o9r)<br /> - [Управление удостоверениями для одного леса гибридных сред с использованием облачной проверки подлинности.](http://aka.ms/g1jat8)<br /> - [Управление рисками с помощью дополнительной многофакторной проверки подлинности для уязвимых приложений.](http://aka.ms/kt1bbm)

## <a name="microsoft-and-third-party-additional-authentication-methods"></a>Корпорация Майкрософт и сторонние дополнительные методы проверки подлинности
Кроме того, можно также настроить и включить Microsoft и методов проверки подлинности сторонних в AD FS в Windows Server 2012 R2. После установки и регистрации с AD FS, вы можете применить многофакторную Идентификацию при настройке политики проверки подлинности глобальных или на конкретных сторон.

Ниже приведен алфавитный список поставщиков Майкрософт и сторонних поставщиков с предложениями многофакторной проверки подлинности, которые в настоящий момент доступны для службы федерации Active Directory в Windows Server 2012 R2.

|Поставщик|Предложение|Ссылки на дополнительные сведения|
|-|-|-| 
|aPersona|aPersona адаптивной многофакторной проверки подлинности для единого входа Microsoft ADFS|[aPersona ASM адаптера AD FS](https://www.apersona.com/adfs)|
|Duo безопасности|Duo адаптера многофакторной проверки Подлинности для AD FS|[Duo проверки подлинности для AD FS](https://duo.com/docs/adfs)|
|Компания Gemalto|Службы идентификации и безопасности компании Gemalto|[http://www.gemalto.com/identity](http://www.gemalto.com/identity)|
|inWebo Technologies|Службы корпоративной проверки подлинности inWebo|[Корпоративная проверка подлинности inWebo](http://www.inwebo.com)|
|Login People|API-соединитель Login People MFA для AD FS 2012 R2 (общедоступная бета-версия)|[https://www.loginpeople.com](https://www.loginpeople.com)|
|Корпорация Майкрософт.|Многофакторная проверка подлинности Microsoft Azure|[Пошаговое руководство. Управление рисками для уязвимых приложений с помощью дополнительной многофакторной проверки подлинности](https://technet.microsoft.com/library/dn280946.aspx) (см. шаг 3).|
Mideye | Поставщик mideye проверки подлинности для служб федерации Active Directory | [Mideye двухфакторной проверки подлинности с помощью служб федерации Microsoft Active Directory](https://www.mideye.com/support/administrators/documentation/integration/microsoft-adfs/)|
|Okta | Okta многофакторной проверки Подлинности для служб федерации Active Directory | [Okta многофакторной проверки Подлинности для Active Directory Federation Services (ADFS)](https://help.okta.com/en/prod/Content/Topics/integrations/adfs-okta-int.htm)|
|Одно удостоверение| Starling 2FA AD FS|[Starling 2FA адаптера AD FS](https://www.oneidentity.com/products/starling-two-factor-authentication/)|
|Одно удостоверение| Защитник AD FS|[Защитник AD FS-адаптер](https://www.oneidentity.com/products/defender/)|
|Компания ping Identity|Адаптер PingID многофакторной проверки Подлинности для AD FS|[Адаптер PingID многофакторной проверки Подлинности для AD FS](https://documentation.pingidentity.com/pingid/pingidAdminGuide/index.shtml#pid_c_PingIDforADFSSSO.html)|
|RSA, подразделение безопасности EMC|Агент проверки подлинности RSA SecurID для служб федерации Microsoft Active Directory|[Агент проверки подлинности RSA SecurID для служб федерации Microsoft Active Directory](http://www.emc.com/security/rsa-securid/rsa-authentication-agents/microsoft-ad-fs.htm)|
|SafeNet, Inc.|Агент службы проверки подлинности SafeNet (SAS) для AD FS|[Служба проверки подлинности SafeNet: Руководство по конфигурации агента AD FS](http://www.safenet-inc.com/resources/integration-guide/data-protection/Safenet_Authentication_Service/SafeNet_Authentication_Service__AD_FS_Agent_Configuration_Guide/?langtype=1033)|
|SecureMFA|Поставщик SecureMFA OTP| [Поставщики проверки подлинности служб федерации Active Directory с несколькими идентификации](https://www.securemfa.com/)|
|Swisscom|Служба проверки подлинности Mobile ID и службы подписей|[Служба проверки подлинности Mobile ID](http://swisscom.ch/mid)|
|Symantec|Служба проверки и защиты идентификации Symantec (VIP)|[Проверка Symantec и идентификатор защиты службы (VIP)](http://www.symantec.com/vip-authentication-service)|
|Trusona|Основные (многофакторной проверки Подлинности без пароля) и исполнительный (Essential + Проверка удостоверения)| [Trusona многофакторной проверки подлинности](https://www.trusona.com/solution-overview/)|


## <a name="custom-authentication-method-for-ad-fs-in-windows-server-2012-r2"></a>Пользовательский метод проверки подлинности для AD FS в Windows Server 2012 R2
Теперь мы предоставляем инструкции по созданию собственного метода проверки подлинности для AD FS в Windows Server 2012 R2. Дополнительные сведения см. в разделе [Создание пользовательского метода проверки подлинности для AD FS в Windows Server 2012 R2](https://go.microsoft.com/fwlink/?LinkID=511980).

## <a name="see-also"></a>См. также
[Управление рисками с помощью дополнительной многофакторной проверки подлинности для уязвимых приложений](Manage-Risk-with-Additional-Multi-Factor-Authentication-for-Sensitive-Applications.md)


