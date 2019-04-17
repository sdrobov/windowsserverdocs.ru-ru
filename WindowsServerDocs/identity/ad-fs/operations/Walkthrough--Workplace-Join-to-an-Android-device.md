---
ms.assetid: a33bd54c-e6db-4b58-8264-c0f34bd8ba39
title: "Пошаговое руководство - присоединение к рабочему месту на устройстве Android"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: cfe26947b6b0de28ea50367f82d52815fff8f323
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="walkthrough-workplace-join-to-an-android-device"></a>Пошаговое руководство: Присоединение к рабочему месту на устройстве Android

>Область применения: Windows Server 2016, Windows Server 2012 R2


## <a name="join-your-device-with-workplace-join"></a>Присоединение устройства с использованием присоединения к рабочему месту

> [!NOTE]
> Присоединение к рабочему месту Android необходим службе Azure Active Directory устройство регистрации. Чтобы принудительно применить условное устройства политики локальной, необходимо развернуть средства синхронизации службы каталогов (DirSync) с включенным параметром обратной записи объект устройства. В настоящее время устройства обратной записи в Active Directory с Azure Active Directory занимает до 3 часа. Таким образом пользователям необходимо дождаться 3 часа для доступа к локальной веб-приложения, после создания рабочей учетной записи. Дополнительные сведения о развертывании регистрации устройств Azure Active Directory службы см. в разделе, [Azure Active Directory Обзор службы регистрации устройств](https://msdn.microsoft.com/library/azure/dn788908.aspx)

#### <a name="create-a-work-account-that-joins-your-device-with-workplace-join"></a>Создайте рабочую учетную запись, которой будет присоединен устройство на присоединение к рабочему месту

1.  Необходимо будет установить приложение для проверки подлинности Azure на устройство для создания рабочей учетной записи, к которому присоединяется вашего устройства с присоединением к рабочему месту. Следующий URL-адрес содержит инструкции о том, как установить приложение Azure authenticator на устройстве с Android и Добавление рабочей учетной записи. Рабочая учетная запись делает устройства Android в надежное устройство и предоставляет единый вход (SSO) в приложениях на устройстве. Можно использовать надежное устройство для доступа к веб-приложений и современным бизнес приложениям согласно рекомендации ИТ-администратору. Дополнительные сведения см. в разделе [проверки подлинности Azure для Android](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to).

## <a name="see-also"></a>См. также:
[Присоединение к рабочему месту с любого устройства для единого входа и эффективной двухфакторной проверки подлинности между приложениями компании](Join-to-Workplace-from-Any-Device-for-SSO-and-Seamless-Second-Factor-Authentication-Across-Company-Applications.md)
[Настройка локального условного доступа с помощью Azure Active Directory службы регистрации для устройств](https://docs.microsoft.com/azure/active-directory/active-directory-device-registration-on-premises-setup)


