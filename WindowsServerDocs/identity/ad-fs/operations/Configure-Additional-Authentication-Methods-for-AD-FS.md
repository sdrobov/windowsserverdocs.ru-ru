---
ms.assetid: ddfbbda3-30ca-4537-af12-667efc6f63ff
title: Настройка дополнительных методов проверки подлинности для службы федерации Active Directory
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 07/26/2019
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: adb587412d65506c35705c5eaa8dbea8c660d117
ms.sourcegitcommit: 9f955be34c641b58ae8b3000768caa46ad535d43
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/27/2019
ms.locfileid: "68590357"
---
# <a name="configure-additional-authentication-methods-for-ad-fs"></a>Настройка дополнительных методов проверки подлинности для службы федерации Active Directory

Для многофакторной проверки подлинности (MFA) необходимо выбрать по крайней мере один дополнительный метод проверки подлинности. По умолчанию в службы федерации Active Directory (AD FS) (AD FS) в Windows Server 2012 R2 можно выбрать проверку подлинности с помощью сертификата (иными словами, аутентификация на основе смарт-карт) в качестве дополнительного метода проверки подлинности.

> [!NOTE]
> Выбирая проверку подлинности сертификата, убедитесь в том, что сертификаты смарт-карт представлены в защищенном виде и имеют требование ввода ПИН-кода.

Знали ли вы, что Microsoft Azure предоставляет аналогичные функциональные возможности в облаке? Подробнее о [решениях для удостоверений Microsoft Azure](http://aka.ms/m2w274).<br /><br />Создайте гибридное решение для удостоверений в Microsoft Azure:<br /> - [Подробнее о многофакторной идентификации Azure.](http://aka.ms/ey6o9r)<br /> - [Управление удостоверениями для гибридных сред с одним лесом с использованием проверки подлинности в облаке.](http://aka.ms/g1jat8)<br /> - [Управление рисками с помощью дополнительной многофакторной проверки подлинности для конфиденциальных приложений.](http://aka.ms/kt1bbm)

## <a name="microsoft-and-third-party-additional-authentication-methods"></a>Корпорация Майкрософт и сторонние дополнительные методы проверки подлинности
Также можно настроить и включить методы проверки подлинности Майкрософт и сторонних производителей в AD FS в Windows Server 2012 R2. После установки и регистрации в AD FS можно применить MFA в рамках глобальной политики проверки подлинности или для отдельной проверяющей стороны.

Ниже приведен алфавитный список поставщиков Майкрософт и сторонних поставщиков с предложениями многофакторной проверки подлинности, которые в настоящий момент доступны для службы федерации Active Directory в Windows Server 2012 R2.

|Поставщик|Предложение|Ссылки на дополнительные сведения|
|-|-|-| 
|аперсона|Аперсона Адаптивная многофакторная проверка подлинности для единого входа Microsoft ADFS|[Адаптер ADFS Аперсона ASM](https://www.apersona.com/adfs)|
|Duo — безопасность|Адаптер MFA для AD FS|[Duo для проверки подлинности AD FS](https://duo.com/docs/adfs)|
|футурае|Набор проверки подлинности футурае для AD FS|[Футурае строгая проверка подлинности](https://futurae.com)|
|Компания Gemalto|Службы идентификации и безопасности компании Gemalto|[http://www.gemalto.com/identity](http://www.gemalto.com/identity)|
|inWebo Technologies|Службы корпоративной проверки подлинности inWebo|[Проверка подлинности Инвебо Enterprise](http://www.inwebo.com)|
|Login People|API-соединитель Login People MFA для AD FS 2012 R2 (общедоступная бета-версия)|[https://www.loginpeople.com](https://www.loginpeople.com)|
|Корпорация Майкрософт.|Многофакторная проверка подлинности Microsoft Azure|[Пошаговое руководство. Управление рисками для уязвимых приложений с помощью дополнительной многофакторной проверки подлинности](https://technet.microsoft.com/library/dn280946.aspx) (см. шаг 3).|
мидэйе | Поставщик проверки подлинности мидэйе для ADFS | [Мидэйе двухфакторная проверка подлинности с помощью Microsoft Active Directory служба федерации](https://www.mideye.com/support/administrators/documentation/integration/microsoft-adfs/)|
|Okta | Okta MFA для службы федерации Active Directory (AD FS) | [Okta MFA для службы федерации Active Directory (AD FS) (ADFS)](https://help.okta.com/en/prod/Content/Topics/integrations/adfs-okta-int.htm)|
|Одно удостоверение| Старлинг 2FA AD FS|[Адаптер AD FS 2FA Старлинг](https://www.oneidentity.com/products/starling-two-factor-authentication/)|
|Одно удостоверение| AD FS защитника|[Адаптер AD FS защитника](https://www.oneidentity.com/products/defender/)|
|Удостоверение проверки связи|Адаптер Пингид MFA для AD FS|[Адаптер Пингид MFA для AD FS](https://documentation.pingidentity.com/pingid/pingidAdminGuide/index.shtml#pid_c_PingIDforADFSSSO.html)|
|RSA, подразделение безопасности EMC|Агент проверки подлинности RSA SecurID для служб федерации Microsoft Active Directory|[Агент проверки подлинности RSA SecurID для Microsoft службы федерации Active Directory (AD FS)](http://www.emc.com/security/rsa-securid/rsa-authentication-agents/microsoft-ad-fs.htm)|
|SafeNet, Inc.|Агент службы проверки подлинности SafeNet (SAS) для AD FS|[Служба проверки подлинности компании SafeNet: Руководство по конфигурации агента AD FS](http://www.safenet-inc.com/resources/integration-guide/data-protection/Safenet_Authentication_Service/SafeNet_Authentication_Service__AD_FS_Agent_Configuration_Guide/?langtype=1033)|
|секуремфа|Поставщик OTP Секуремфа| [Поставщики многофакторной идентификации ADFS](https://www.securemfa.com/)|
|Swisscom|Служба проверки подлинности Mobile ID и службы подписей|[Служба проверки подлинности с ИД мобильного устройства](http://swisscom.ch/mid)|
|Symantec|Служба проверки и защиты идентификации Symantec (VIP)|[Проверка Symantec и служба защиты идентификации (VIP)](http://www.symantec.com/vip-authentication-service)|
|трусона|Важными (незащищенные паролем MFA) и Executive (основы проверки личности)| [Многофакторная идентификация трусона](https://www.trusona.com/solution-overview/)|


## <a name="custom-authentication-method-for-ad-fs-in-windows-server-2012-r2"></a>Пользовательский метод проверки подлинности для AD FS в Windows Server 2012 R2
Теперь мы предоставляем инструкции по созданию собственного метода проверки подлинности для AD FS в Windows Server 2012 R2. Дополнительные сведения см. в разделе [Создание пользовательского метода проверки подлинности для AD FS в Windows Server 2012 R2](https://go.microsoft.com/fwlink/?LinkID=511980).

## <a name="see-also"></a>См. также
[Управление рисками для уязвимых приложений с помощью дополнительной многофакторной аутентификации](Manage-Risk-with-Additional-Multi-Factor-Authentication-for-Sensitive-Applications.md)


