---
title: AD FS Устранение неполадок — инициированном поставщиком удостоверений для входа
description: В этом документе описывается устранение неполадок на странице входа AD FS.
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 01/03/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 61e9adc708e95a6ab4a82550280737b2f4bad0a1
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59844945"
---
# <a name="ad-fs-troubleshooting---idp-initiated-sign-on"></a>AD FS Устранение неполадок — инициированном поставщиком удостоверений для входа
Страницы входа AD FS можно использовать для тестирования независимо от того, имеется ли работа проверки подлинности.  Для этого перейдите на страницу и входа в систему.  Кроме того можно использовать страницы входа для проверки, что указаны все проверяющие стороны SAML 2.0.

## <a name="enable-the-idp-intiated-sign-on-page"></a>Включение входа инициируемого поставщиком удостоверений на странице
По умолчанию AD FS в Windows 2016 не имеет знак на странице "включено".  Чтобы включить его можно использовать команду PowerShell Set-AdfsProperties.  Используйте следующую процедуру для включения страницы:

1.  Откройте Windows PowerShell
2.  Введите: `Get-AdfsProperties` и нажмите клавишу ВВОД
3.  Убедитесь, что **EnableIdpInitiatedSignonPage** имеет значение false ![False](media/ad-fs-tshoot-initiatedsignon/idp2.png)
4.  В PowerShell введите следующую команду:  `Set-AdfsProperties -EnableIdpInitiatedSignonPage $true`
5.  Вы не увидите подтверждение таким образом, введите Get-AdfsProperties еще раз и убедитесь, что **EnableIdpInitatedSignonPage** задано значение true.
![Значение true](media/ad-fs-tshoot-initiatedsignon/idp4.png)

## <a name="test-authentication"></a>Тест проверки подлинности
Используйте следующую процедуру, чтобы протестировать аутентификацию на основе AD FS на страницу входа Idp-Initiated.

1.  Откройте веб-браузер и перейдите на страницу входа поставщика удостоверений.  Пример:  https://sts.contoso.com/adfs/ls/idpinitiatedsignon.htm
2.  Вам следует запрос на вход.  Введите свои учетные данные.
![вход](media/ad-fs-tshoot-initiatedsignon/idp5.png)
3.  Если это прошла успешно, вы должны войти.


## <a name="test-authentication-using-a-seamless-logon-experience"></a>Тестирование проверки подлинности, используя возможности входа
Варианты простого входа в систему можно проверить, убедившись, что URL-адреса для серверов AD FS добавляются в зону локальной интрасети из вашего браузера.  Используйте следующую процедуру.

1.  На клиенте Windows 10 нажмите кнопку Пуск и введите свойства обозревателя и выберите Свойства обозревателя.
2.   Щелкните вкладку «Безопасность», щелкните локальной интрасети и нажмите кнопку "узлы".
![Простой](media/ad-fs-tshoot-initiatedsignon/idp8.png)
1.  Нажмите кнопку Дополнительно.
2.  Введите URL-адрес и щелкните "Добавить".  Нажмите кнопку Закрыть.
![Добавьте URL-адрес](media/ad-fs-tshoot-initiatedsignon/idp9.png)
1.  Нажмите кнопку ОК.  Нажмите кнопку ОК.  Это следует закрывать свойства обозревателя.
2.  Откройте веб-браузер и перейдите на страницу входа поставщика удостоверений.  Пример:  https://sts.contoso.com/adfs/ls/idpinitiatedsignon.htm
3.  Нажмите кнопку входа.  Вы должны включить автоматический вход и не будут запрошены учетные данные.
![Простой](media/ad-fs-tshoot-initiatedsignon/idp6.png)

## <a name="next-steps"></a>Следующие шаги

- [Устранение неполадок AD FS](ad-fs-tshoot-overview.md)