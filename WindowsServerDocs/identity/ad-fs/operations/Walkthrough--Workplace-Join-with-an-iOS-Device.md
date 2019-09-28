---
ms.assetid: 299e4fb9-8f1a-4275-ad7d-dad4f1594657
title: Пошаговое руководство. Workplace Join с устройством iOS
description: ''
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 10/18/2018
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 5214165c2843461a2da8b574ad28f92b0e0bc64d
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71407494"
---
# <a name="walkthrough-workplace-join-with-an-ios-device"></a>Пошаговое руководство: присоединение к рабочему месту с устройства iOS


> [!IMPORTANT] 
> Этот метод относится только к полностью локальным клиентам. Гибридные или облачные пользователи не должны использовать этот метод для регистрации устройств iOS. Этот метод несовместим, если локальные клиенты решили перейти в облако. Необходимо отменить регистрацию устройства и зарегистрировать его в облаке. 

В этом разделе показано присоединение к рабочему месту с устройства iOS. Чтобы ознакомиться с этим пошаговым руководством, необходимо выполнить действия, описанные в разделе [Настройка лабораторной среды для AD FS в Windows Server 2012 R2](../../ad-fs/deployment/Set-up-the-lab-environment-for-AD-FS-in-Windows-Server-2012-R2.md) . Вы можете использовать устройство для доступа к тому же веб-приложению компании, к которому вы обращались в [Walkthrough: Workplace Join с устройством Windows @ no__t-0.


## <a name="join-an-ios-device-with-workplace-join"></a>Присоединение устройства iOS c использованием функции присоединения к рабочему месту

> [!IMPORTANT]
> Если настроена локальная DRS, устройство iOS должно доверять SSL-сертификату, который использовался для настройки службы федерации Active Directory (AD FS) (AD FS) в [Step 2: Настройте сервер федерации (ADFS1) со службой регистрации устройств @ no__t-0, чтобы Workplace Join для успешности.
> 
> -   Если SSL-сертификат AD FS был издан тестовым центром сертификации, необходимо установить сертификат центра сертификации на устройство iOS.
> -   Если сертификат центра сертификации опубликован на веб-сайте, можно перейти на веб-сайт с устройства iOS и установить этот сертификат.

В этой демонстрации устройство присоединяется к рабочему месту.

#### <a name="to-join-an-ios-device-to-a-workplace"></a>Присоединение устройства iOS к рабочему месту

1. -   **Когда настроенное DRS является служба регистрации устройств Azure Active Directory, выполните следующие действия.** Откройте Apple Safari и перейдите к Регистрация устройств Azure Active Directory Service в качестве конечной точки профиля для устройств iOS, < `https://enterpriseregistration.windows.net/enrollmentserver/otaprofile/<yourdomainname` > где < `yourdomainname` > — это доменное имя, настроенное с Azure Active Directory. Например, если имя домена contoso.com, URL-адрес будет: `https://enterpriseregistration.windows.net/enrollmentserver/otaprofile/contoso.com`

   -   **Когда настроенной DRS является локальная DRS, выполните следующие действия.** Откройте Apple Safari и перейдите к конечной точке "служба регистрации устройств" (DRS), переданной в конечную точку профиля для устройств iOS, `https://adf1s.contoso.com/enrollmentserver/otaprofile`

   Существует много способов взаимодействия с этим URL-адресом для ваших пользователей. Один из рекомендованных способов — опубликовать этот URL-адрес в настраиваемом сообщении об отказе в доступе к приложению в AD FS. Это рассматривается в следующем разделе: [Создание политики доступа к приложениям и пользовательского сообщения об отказе в доступе](https://docs.microsoft.com/azure/active-directory/active-directory-device-registration-on-premises-setup#create-an-application-access-policy-and-custom-access-denied-message)

2. Войдите на веб-страницу с помощью учетной записи домена организации: <strong>roberth@contoso.com</strong> и пароль: <strong>P@ssword</strong>.

3. Система предложит установить профиль. На экране **Установка профиля** щелкните **Установить**.

4. В ответ на запрос подтверждения установки профиля щелкните **Установить сейчас**.

5. Если устройство требует ввода PIN-кода для разблокировки, система предложит ввести PIN-код.

6. Установка профиля завершена, когда отобразится экран **Профиль установлен** . Нажмите кнопку **Готово**.

   Вернитесь в Safari. Отобразится сообщение о том, что Safari можно закрыть или выйти из приложения.

> [!TIP]
> Для просмотра или удаления профиля присоединения к рабочему месту найдите раздел **Параметры**, щелкните **Общие**, а затем — **Профили** на устройстве iOS.

## <a name="see-also"></a>См. также


- [Присоединение к рабочей области с любого устройства для единого входа и эффективная двухфакторная аутентификация в приложениях компании](Join-to-Workplace-from-Any-Device-for-SSO-and-Seamless-Second-Factor-Authentication-Across-Company-Applications.md)
- [Настройка лабораторной среды для служб федерации Active Directory в Windows Server 2012 R2](../../ad-fs/deployment/Set-up-the-lab-environment-for-AD-FS-in-Windows-Server-2012-R2.md)
- [Пошаговое руководство: Присоединение к рабочему месту с устройства Windows](Walkthrough--Workplace-Join-with-a-Windows-Device.md)



