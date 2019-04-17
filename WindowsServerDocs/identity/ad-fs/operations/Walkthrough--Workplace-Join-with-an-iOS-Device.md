---
ms.assetid: 299e4fb9-8f1a-4275-ad7d-dad4f1594657
title: Пошаговое руководство - присоединение к рабочему месту с устройства iOS
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 0a8643bab913dfec07c6bbea0c068e1240f16c5b
ms.sourcegitcommit: a2260c96b0e49519d180c7382b921ce8ddb053fe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2018
---
# <a name="walkthrough-workplace-join-with-an-ios-device"></a>Пошаговое руководство: Присоединение к рабочему месту с устройства iOS

>Область применения: Windows Server 2012 R2

В этом разделе показано присоединение к рабочему месту с устройства iOS. Необходимо выполнить действия, описанные в [Настройка лабораторной среды для служб AD FS в Windows Server 2012 R2](../../ad-fs/deployment/Set-up-the-lab-environment-for-AD-FS-in-Windows-Server-2012-R2.md) статьи до начала выполнения данного пошагового руководства. Устройство можно использовать для доступа к же веб-приложению компании, что и в [Пошаговое руководство: присоединение к рабочему месту с устройства Windows](Walkthrough--Workplace-Join-with-a-Windows-Device.md).

## <a name="join-an-ios-device-with-workplace-join"></a>Присоединение устройства iOS с использованием присоединения к рабочему месту

> [!IMPORTANT]
> При настройке локальной DRS устройство iOS должно доверять сертификату Secure Socket Layer (SSL), которая использовалась для настройки служб федерации Active Directory (AD FS) в [шаг 2: Настройка сервера федерации (ADFS1) with Device Registration Service](../../ad-fs/deployment/Set-up-the-lab-environment-for-AD-FS-in-Windows-Server-2012-R2.md#BKMK_4), для успешного присоединения к рабочему месту.
> 
> -   Если сертификат AD FS SSL был издан тестовым центром сертификации (ЦС), необходимо установить сертификат центра сертификации на устройство iOS.
> -   Если сертификат центра сертификации опубликован на веб-сайте, можно перейти на веб-сайт с устройства iOS и установить сертификат.

В этой демонстрации устройство присоединяется к рабочему месту.

#### <a name="to-join-an-ios-device-to-a-workplace"></a>Присоединение устройства iOS к рабочему месту

1.  -   **Когда настроенное DRS является служба регистрации устройств Azure Active Directory:** откройте Apple Safari и перейдите к конечной точке беспроводного профиля службы регистрации устройств Azure Active Directory для устройств iOS <`https://enterpriseregistration.windows.net/enrollmentserver/otaprofile/<yourdomainname` > где <`yourdomainname`> — имя домена, настроенного с Azure Active Directory. Например если имя домена contoso.com, URL-адрес будет: `https://enterpriseregistration.windows.net/enrollmentserver/otaprofile/contoso.com`

    -   **Когда настроенное DRS является локальная DRS**: Откройте Apple Safari и перейдите к конечной точке беспроводного профиля службы регистрации устройств (DRS) для устройств iOS`https://adf1s.contoso.com/enrollmentserver/otaprofile`

    Существует много способов взаимодействия этот URL-адрес для пользователей. Один из рекомендованных способов — опубликовать этот URL-адрес в access пользовательского приложения об отказе в доступе сообщение в AD FS. Это рассматривается в следующем разделе: [Создание политики доступа к приложениям и настраиваемого сообщения об отказе в доступе](https://docs.microsoft.com/azure/active-directory/active-directory-device-registration-on-premises-setup#create-an-application-access-policy-and-custom-access-denied-message)

2.  Войдите в систему веб-страницы, используя учетную запись домена организации: ** roberth@contoso.com ** и пароль: ** P@ssword **.

3.  Вам будет предложено установить профиль. На **установить профиль** нажмите кнопку **установить**.

4.  Ответ на запрос подтверждения установки профиля щелкните **установить сейчас**.

5.  Если устройству требуется ПИН-код для разблокировки устройства, вам будет предложено ввести ПИН-код.

6.  Установка профиля завершена в том случае, когда вы видите **установлен профиль** экрана. Нажмите кнопку **сделать**.

    Вернитесь в Safari. Сообщение о том, что вы можете закрыть или выйти из Safari.

> [!TIP]
> Для просмотра или удаления профиля присоединения к рабочему месту, перейдите к **параметры**, нажмите кнопку **Общие**, а затем нажмите кнопку **профили** на устройстве iOS.

## <a name="see-also"></a>См. также:


- [Присоединение к рабочему месту с любого устройства для единого входа и эффективная двухфакторная аутентификация в приложениях компании](Join-to-Workplace-from-Any-Device-for-SSO-and-Seamless-Second-Factor-Authentication-Across-Company-Applications.md)
- [Настройка лабораторной среды для служб AD FS в Windows Server 2012 R2](../../ad-fs/deployment/Set-up-the-lab-environment-for-AD-FS-in-Windows-Server-2012-R2.md)
- [Пошаговое руководство: Присоединение к рабочему месту с устройства Windows](Walkthrough--Workplace-Join-with-a-Windows-Device.md)



