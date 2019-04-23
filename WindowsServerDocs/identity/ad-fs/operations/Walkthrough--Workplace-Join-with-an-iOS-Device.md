---
ms.assetid: 299e4fb9-8f1a-4275-ad7d-dad4f1594657
title: Пошаговое руководство. присоединение к рабочему месту с устройства iOS
description: ''
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 10/18/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: c9c66b5bbe5fff83010859abe6ea4759d5bc4be0
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59853635"
---
# <a name="walkthrough-workplace-join-with-an-ios-device"></a>Пошаговое руководство: присоединение к рабочему месту с устройства iOS

>Область применения. Windows Server 2012 R2

> [!IMPORTANT] 
> Этот метод является касается только полностью в локальной среде клиентов. Гибридного или только для облака клиенты должны не этот метод позволяет регистрировать устройства iOS. И этот метод не совместима, когда клиенты в локальной среде решите перейти в облако. Устройство необходимо отменить регистрацию и зарегистрировать с облаком. 

В этом разделе показано присоединение к рабочему месту с устройства iOS. Необходимо выполнить действия, описанные в [Настройка лабораторной среды для AD FS в Windows Server 2012 R2](../../ad-fs/deployment/Set-up-the-lab-environment-for-AD-FS-in-Windows-Server-2012-R2.md) разделе до начала выполнения данного пошагового руководства. Устройства можно использовать для доступа к тем же веб-приложению компании, что и в [Пошаговое руководство: Присоединение к рабочему месту с устройства Windows](Walkthrough--Workplace-Join-with-a-Windows-Device.md).


## <a name="join-an-ios-device-with-workplace-join"></a>Присоединение устройства iOS c использованием функции присоединения к рабочему месту

> [!IMPORTANT]
> При настройке локальной DRS устройство iOS должно доверять сертификата Secure Socket Layer (SSL), который использовался для настройки служб федерации Active Directory (AD FS) в [шаг 2: Настройка сервера федерации (ADFS1) with Device Registration Service](../../ad-fs/deployment/Set-up-the-lab-environment-for-AD-FS-in-Windows-Server-2012-R2.md#BKMK_4), для успешного присоединения к рабочему месту.
> 
> -   Если SSL-сертификат AD FS был издан тестовым центром сертификации, необходимо установить сертификат центра сертификации на устройство iOS.
> -   Если сертификат центра сертификации опубликован на веб-сайте, можно перейти на веб-сайт с устройства iOS и установить этот сертификат.

В этой демонстрации устройство присоединяется к рабочему месту.

#### <a name="to-join-an-ios-device-to-a-workplace"></a>Присоединение устройства iOS к рабочему месту

1.  -   **Когда настроенное DRS является служба регистрации устройств Azure Active Directory, выполните следующие действия.** Откройте Apple Safari и перейдите к конечной точке беспроводного профиля службы регистрации устройств Azure Active Directory для устройств iOS <`https://enterpriseregistration.windows.net/enrollmentserver/otaprofile/<yourdomainname` > где <`yourdomainname`> — имя домена, которое вы настроили в Azure Active Directory. Например, если имя домена contoso.com, URL-адрес будет: `https://enterpriseregistration.windows.net/enrollmentserver/otaprofile/contoso.com`

    -   **Когда настроенной DRS является локальная DRS, выполните следующие действия.** Откройте Apple Safari и перейдите к конечной точке беспроводного профиля службы регистрации устройств (DRS) для устройств iOS `https://adf1s.contoso.com/enrollmentserver/otaprofile`

    Существует много способов взаимодействия с этим URL-адресом для ваших пользователей. Один из рекомендованных способов — опубликовать этот URL-адрес в настраиваемом сообщении об отказе в доступе к приложению в AD FS. Это рассматривается в следующем разделе: [Создание политики доступа к приложениям и пользовательского сообщения об отказе в доступе](https://docs.microsoft.com/azure/active-directory/active-directory-device-registration-on-premises-setup#create-an-application-access-policy-and-custom-access-denied-message)

2.  Войдите на веб-страницу с помощью доменной учетной записью компании: **roberth@contoso.com** и пароль: **P@ssword**.

3.  Система предложит установить профиль. На экране **Установка профиля** щелкните **Установить**.

4.  В ответ на запрос подтверждения установки профиля щелкните **Установить сейчас**.

5.  Если устройство требует ввода PIN-кода для разблокировки, система предложит ввести PIN-код.

6.  Установка профиля завершена, когда отобразится экран **Профиль установлен** . Нажмите кнопку **Готово**.

    Вернитесь в Safari. Отобразится сообщение о том, что Safari можно закрыть или выйти из приложения.

> [!TIP]
> Для просмотра или удаления профиля присоединения к рабочему месту найдите раздел **Параметры**, щелкните **Общие**, а затем — **Профили** на устройстве iOS.

## <a name="see-also"></a>См. также


- [Присоединение к рабочему месту с любого устройства для единого входа и эффективная двухфакторная аутентификация в приложениях компании](Join-to-Workplace-from-Any-Device-for-SSO-and-Seamless-Second-Factor-Authentication-Across-Company-Applications.md)
- [Настройка лабораторной среды для AD FS в Windows Server 2012 R2](../../ad-fs/deployment/Set-up-the-lab-environment-for-AD-FS-in-Windows-Server-2012-R2.md)
- [Пошаговое руководство: Присоединение к рабочему месту с устройства Windows](Walkthrough--Workplace-Join-with-a-Windows-Device.md)



