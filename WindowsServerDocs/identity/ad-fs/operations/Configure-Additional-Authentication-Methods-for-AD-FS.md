---
ms.assetid: ddfbbda3-30ca-4537-af12-667efc6f63ff
title: "Настройка дополнительных методов проверки подлинности для AD FS"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 65baa6f94e1efa1fa337eab477b18f947cf0bb2d
ms.sourcegitcommit: 36d7b1dfd7da8e9f303d007a628e76149de000f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2018
---
# <a name="configure-additional-authentication-methods-for-ad-fs"></a>Настройка дополнительных методов проверки подлинности для AD FS

>Область применения: Windows Server 2016, Windows Server 2012 R2

Чтобы включить многофакторную проверку подлинности (MFA), необходимо выбрать по крайней мере один дополнительного метода проверки подлинности. По умолчанию в федерации служб Active Directory (AD FS) в Windows Server 2012 R2 в качестве дополнительного метода проверки подлинности можно выбрать сертификат проверки подлинности (другими словами, смарт карта).

> [!NOTE]
> При выборе проверки подлинности сертификата, убедитесь, что сертификаты смарт-карт были представлены в защищенном виде и имеют требования к ПИН-код.

Знаете ли вы, что Microsoft Azure предоставляет аналогичные функциональные возможности в облаке? Дополнительные сведения о [решениях для удостоверений Microsoft Azure ](http://aka.ms/m2w274).<br /><br />Создайте гибридное решение для удостоверений в Microsoft Azure:<br /> - [Сведения о многофакторной проверки подлинности Azure.](http://aka.ms/ey6o9r)<br /> - [Управление удостоверениями для одного леса гибридных сред с использованием проверки подлинности в облаке.](http://aka.ms/g1jat8)<br /> - [Управление рисками с помощью дополнительной многофакторной проверки подлинности для уязвимых приложений.](http://aka.ms/kt1bbm)|

## <a name="microsoft-and-third-party-additional-authentication-methods"></a>Корпорация Майкрософт и сторонние дополнительные методы проверки подлинности
Можно также настроить и включить Майкрософт и сторонние методы в AD FS в Windows Server 2012 R2. После установки и регистрируются с помощью службы федерации Active Directory, можно обеспечить принудительное многофакторной проверки Подлинности в рамках политики проверки подлинности глобальной или каждого полагаться производителей.

Ниже приведен алфавитный список поставщиков Майкрософт и сторонних поставщиков с предложениями многофакторной проверки Подлинности в настоящее время доступны для AD FS в Windows Server 2012 R2.

||||
|-|-|-|
|**Поставщик**|**Предложения**|**Ссылки на дополнительные**|
|Компания Gemalto|Удостоверение службы безопасности компании Gemalto|[http://www.gemalto.com/identity](http://www.gemalto.com/identity)|
|inWebo технологии|Корпоративной проверки подлинности inWebo|[Корпоративная проверка подлинности inWebo](http://www.inwebo.com)|
|Имя входа пользователей|Люди многофакторную проверку Подлинности API-соединитель Login для AD FS 2012 R2 (общедоступная бета-версия)|[https://www.loginpeople.com](https://www.loginpeople.com)|
|Корпорация Майкрософт.|Многофакторная проверка Подлинности Microsoft Azure|[Пошаговое руководство: Управление рисками для уязвимых приложений с помощью дополнительной многофакторной проверки подлинности](https://technet.microsoft.com/library/dn280946.aspx) (см. шаг 3.)|
|RSA, подразделение безопасности EMC|Агент проверки подлинности RSA SecurID для служб федерации Microsoft Active Directory|[Агент проверки подлинности RSA SecurID для служб федерации Microsoft Active Directory](http://www.emc.com/security/rsa-securid/rsa-authentication-agents/microsoft-ad-fs.htm)|
|SafeNet, Inc.|Агент службы (SAS) для проверки подлинности SafeNet для служб AD FS|[Служба проверки подлинности SafeNet: Руководство по конфигурации агента AD FS](http://www.safenet-inc.com/resources/integration-guide/data-protection/Safenet_Authentication_Service/SafeNet_Authentication_Service__AD_FS_Agent_Configuration_Guide/?langtype=1033)|
|Swisscom|Служба проверки подлинности Mobile ID и службы подписей|[Служба проверки подлинности Mobile ID](http://swisscom.ch/mid)|
|Symantec|Symantec служба проверки и идентификатор защиты (VIP)|[Symantec служба проверки и идентификатор защиты (VIP)](http://www.symantec.com/vip-authentication-service)|

## <a name="custom-authentication-method-for-ad-fs-in-windows-server-2012-r2"></a>Пользовательский метод проверки подлинности для AD FS в Windows Server 2012 R2
Теперь мы предоставляем инструкции по созданию собственного метода проверки подлинности для AD FS в Windows Server 2012 R2. Дополнительные сведения см. в разделе [Создание пользовательского метода проверки подлинности для AD FS в Windows Server 2012 R2](https://go.microsoft.com/fwlink/?LinkID=511980).

## <a name="see-also"></a>См. также:
[Управление рисками с помощью дополнительной многофакторной проверки подлинности для уязвимых приложений](Manage-Risk-with-Additional-Multi-Factor-Authentication-for-Sensitive-Applications.md)


