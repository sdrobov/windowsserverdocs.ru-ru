---
title: Устранение неполадок AD FS. разрешение DNS
description: В этом документе описывается, как устранять неполадки в DNS-аспектах AD FS
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 01/03/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 7ffda6916bd91f1195ac0c289959becafff1d2c5
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71407205"
---
# <a name="ad-fs-troubleshooting---dns"></a>Устранение неполадок AD FS — DNS 
Одно из первых проверок, если AD FS не работает или не отвечает, является разрешением DNS-имен.  Это базовые тесты, позволяющие определить, находятся ли AD FS серверы или серверы WAP в сети.  Для внутренних пользователей эти тесты должны разрешаться на AD FS серверы (STS).    Для внешних пользователей эти тесты должны разрешаться на серверы WAP.

В оставшейся части этого документа будет показано, как выполнять некоторые проверки быстрого разрешения имен с помощью программ командной строки.

## <a name="ping-test"></a>Проверка связи
Проверяет подключение на уровне IP к другому компьютеру TCP/IP, отправляя сообщения эхо-запросов протокола ICMP. Отображаются сообщения о получении соответствующих эхо-ответов, а также время кругового пути.  Дополнительные сведения см. в разделе [Проверка связи](https://technet.microsoft.com/library/ff961503.aspx).


>[!NOTE]
>Имейте в виду, что некоторые организации блокируют этот порт на своих серверах, и вы можете получить ответ **время ожидания запроса** .

### <a name="to-use-a-ping-test"></a>Использование проверки связи
1.  Открытие командной строки
2. Введите PING <name of adfs server> a. Пример.  Проверка связи sts.contoso.com
3. Вы должны увидеть ответ от сервера

![Ping](media/ad-fs-tshoot-dns/dns1.png)

## <a name="nslookup"></a>Программы
Отображает сведения, которые можно использовать для диагностики инфраструктуры системы доменных имен (DNS).  Дополнительные сведения см. в разделе [nslookup](https://technet.microsoft.com/library/cc725991.aspx).

### <a name="to-use-a-nslookup"></a>Использование NSLookup
1.  Открытие командной строки
2. Введите PING <name of adfs server> a. Пример: nslookup sts.contoso.com
3. Вы должны увидеть сведения о DNS для сервера ![NSLookup @ no__t-1.

## <a name="tracert"></a>Tracert
Определяет путь, полученный к назначению путем отправки эхо-запроса протокола ICMP или ICMPv6-сообщений в назначение с добавочным увеличением срока жизни (TTL) значений полей.   Дополнительные сведения см. в разделе [tracert](https://technet.microsoft.com/library/ff961507.aspx).


### <a name="to-use-tracert"></a>Использование tracert
1.  Открытие командной строки
2. Введите tracert <name of adfs server> a. Пример: tracert sts.contoso.com
3. Вы должны увидеть путь назначения, используемый для доступа к серверу ![Tracert @ no__t-1.

## <a name="next-steps"></a>Следующие шаги

- [Устранение неполадок в AD FS](ad-fs-tshoot-overview.md)