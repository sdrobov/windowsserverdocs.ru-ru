---
ms.assetid: a33bd54c-e6db-4b58-8264-c0f34bd8ba39
title: Пошаговое руководство. присоединение к рабочему месту на устройстве Android
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: cfe26947b6b0de28ea50367f82d52815fff8f323
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59873835"
---
# <a name="walkthrough-workplace-join-to-an-android-device"></a>Пошаговое руководство: Присоединение к рабочему месту на устройстве Android

>Область применения. Windows Server 2016, Windows Server 2012 R2


## <a name="join-your-device-with-workplace-join"></a>Присоединение устройства с использованием функции присоединения к рабочему месту

> [!NOTE]
> Android присоединение к рабочему месту требуется Azure Active Directory службы регистрации для устройств. Чтобы применить условные политики локальное устройство, инструмент синхронизации каталогов (DirSync) должны быть развернуты с включенным параметром обратной записью объектов устройств. В настоящее время обратную запись устройств в Active Directory из Azure Active Directory занимает до 3 часов. Таким образом пользователям придется ждать 3 часа для доступа к локальным веб-приложения, после создания рабочей учетной записи. Дополнительные сведения о развертывании регистрации устройств Azure Active Directory service, см. в разделе, [Azure Active Directory Обзор службы регистрации устройств](https://msdn.microsoft.com/library/azure/dn788908.aspx)

#### <a name="create-a-work-account-that-joins-your-device-with-workplace-join"></a>Создание рабочей учетной записи, который присоединяет устройства с помощью workplace Join

1.  Необходимо установить приложение Azure Authenticator на устройстве, чтобы создать рабочую учетную запись, который соединяется с присоединение к рабочему месту устройства. Следующий URL-адрес содержит инструкции о том, как установить приложение Azure authenticator на устройстве Android и добавить рабочую учетную запись. Рабочая учетная запись делает устройства Android в доверенное устройство и предоставляет единый вход (SSO) для приложений на устройствах. Можно использовать надежное устройство для доступа к веб-приложений и современных бизнес-приложений, согласно рекомендациям ИТ-администратору. Дополнительные сведения см. в разделе [Azure Authenticator для Android](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to).

## <a name="see-also"></a>См. также
[Присоединение к рабочему месту с любого устройства для единого входа и эффективная двухфакторная проверка подлинности между компании приложениях](Join-to-Workplace-from-Any-Device-for-SSO-and-Seamless-Second-Factor-Authentication-Across-Company-Applications.md)
[Настройка локального условного доступа с помощью Azure Active Directory службы регистрации для устройств](https://docs.microsoft.com/azure/active-directory/active-directory-device-registration-on-premises-setup)


