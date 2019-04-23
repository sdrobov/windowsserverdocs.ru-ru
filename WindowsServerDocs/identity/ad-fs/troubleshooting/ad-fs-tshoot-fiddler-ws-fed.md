---
title: AD FS, устранение неполадок - Fiddler - WS-Federation
description: В этом документе показаны подробные трассировки обмена WS-Federation с AD FS
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 01/18/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: be1c9f466ec13272d10f0fb9ca31cf326a1ec29a
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59846905"
---
# <a name="ad-fs-troubleshooting---fiddler---ws-federation"></a>AD FS, устранение неполадок - Fiddler - WS-Federation
![](media/ad-fs-tshoot-fiddler-ws-fed/fiddler9.png)

## <a name="step-1-and-2"></a>Шаг 1 и 2
Это начало наших трассировки.  В этом кадре вы увидите следующее: ![](media/ad-fs-tshoot-fiddler-ws-fed/fiddler1.png)

Запрос:

- Запрос HTTP GET для наших доверяющей стороной (http://sql1.contoso.com/SampApp)

Ответ:

- Ответ — HTTP 302 (перенаправление).  Передачи данных в заголовке ответа показано, где для перенаправления)https://sts.contoso.com/adfs/ls)
- URL-адрес перенаправления содержит wa = wsignin 1.0, который сообщает, что наше приложение RP встроенные запроса входа WS-Federation для нас и отправляемые /adfs в ADFS/ls/конечной точки.  Это известно как перенаправления привязки.
![](media/ad-fs-tshoot-fiddler-ws-fed/fiddler2.png)

## <a name="step-3-and-4"></a>Шаг 3 и 4

![](media/ad-fs-tshoot-fiddler-ws-fed/fiddler3.png)

Запрос:

- Запрос HTTP GET для наших server(sts.contoso.com) AD FS

Ответ:

- Ответ — запрос учетных данных.  Это означает, что мы используем проверку подлинности форм
- Щелкнув WebView ответа отобразится запрос учетных данных.
![](media/ad-fs-tshoot-fiddler-ws-fed/fiddler6.png)

## <a name="step-5-and-6"></a>Шаг 5 и 6

![](media/ad-fs-tshoot-fiddler-ws-fed/fiddler4.png)

Запрос:

- HTTP POST с именем пользователя и пароль.  
- Мы представляем наши учетные данные.  Взглянув на необработанные данные в запросе мы видим, учетные данные

Ответ:

- Ответ будет обнаружен и MSIAuth создается и возвращается зашифрованного файла cookie.  Это используется для проверки утверждения SAML, созданного клиента.  Это также называется «файла cookie проверки подлинности» и появятся только при поставщика удостоверений AD FS.


## <a name="step-7-and-8"></a>Шаг 7 и 8
![](media/ad-fs-tshoot-fiddler-ws-fed/fiddler5.png)

Запрос:

- Теперь, когда мы прошли проверку подлинности мы другой запрос HTTP GET для сервера AD FS и представить наш маркер аутентификации

Ответ:

- Ответ — HTTP ОК, это означает, что AD FS подлинности пользователя, по которой указанные учетные данные
- Кроме того задается 3 файла cookie обратно клиенту
    - MSISAuthenticated содержит значение timestamp в кодировке base 64 для при аутентификации клиента.
    - MSISLoopDetectionCookie используется механизм определения бесконечного цикла AD FS клиентам stop, дойти до в бесконечного цикла перенаправлений на сервере федерации. Данные cookie представляет собой метку времени, который хранится в кодировке Base64.
    - MSISSignout используется для отслеживания поставщика удостоверений и посещены все поставщики ресурсов для сеанса единого входа. Этот файл cookie используется при вызове выхода WS-Federation. Вы увидите содержимое этого файла cookie, с помощью декодер base64.
    
## <a name="step-9-and-10"></a>Шаг 9 и 10
![](media/ad-fs-tshoot-fiddler-ws-fed/fiddler7.png) Запрос:

- HTTP POST

Ответ:

- Ответ будет обнаружен

## <a name="step-11-and-12"></a>Шаг 11 и 12
![](media/ad-fs-tshoot-fiddler-ws-fed/fiddler8.png) Запрос:

- HTTP GET

Ответ:

- Ответ — ОК

## <a name="next-steps"></a>Следующие шаги

- [Устранение неполадок AD FS](ad-fs-tshoot-overview.md)