---
title: AD FS Устранение неполадок — разрешение DNS
description: В этом документе описывается устранение неполадок DNS аспекты AD FS
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 01/03/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 7e0065feac4241b617b8b13c6867d5dc36634bd0
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59815905"
---
# <a name="ad-fs-troubleshooting---dns"></a>AD FS Устранение неполадок — DNS 
В первую очередь, чтобы проверить, если AD FS не работает или не отвечает, он разрешения имен DNS.  Ниже приведены основные тесты, чтобы определить, если серверы AD FS или WAP-серверы были обнаружены в сети.  Для внутренних пользователей эти тесты следует разрешить к серверам AD FS (STS).    Для внешних пользователей эти тесты следует разрешить WAP-серверах.

Далее в этом документе показано, как провести некоторые проверки разрешения краткое имя, с помощью средства командной строки.

## <a name="ping-test"></a>Проверки связи
Проверяет возможность подключения на уровне IP-адрес к другому компьютеру TCP/IP путем отправки сообщений запроса проверки связи Internet Control Message Protocol (ICMP). Отображаются получения соответствующего сообщения ответа проверки связи, а также время кругового пути.  Дополнительные сведения см. в разделе [Ping](https://technet.microsoft.com/library/ff961503.aspx).


>[!NOTE]
>Имейте в виду, что некоторые организации блокируют этот порт на их серверах, и вы можете получить **истекло время ожидания запроса** ответа.

### <a name="to-use-a-ping-test"></a>Для использования проверки СВЯЗИ
1.  Откройте командную строку
2. Введите PING <name of adfs server> . Пример.  PING sts.contoso.com
3. Вы увидите ответ от сервера

![Ping](media/ad-fs-tshoot-dns/dns1.png)

## <a name="nslookup"></a>NSLookup
Отображает сведения, которые можно использовать для диагностики инфраструктуры доменных имен (DNS).  Дополнительные сведения см. в разделе [NSLookup](https://technet.microsoft.com/library/cc725991.aspx).

### <a name="to-use-a-nslookup"></a>Использование команды NSLookup
1.  Откройте командную строку
2. Введите PING <name of adfs server> . Пример: sts.contoso.com nslookup
3. Вы должны увидеть сведения о dns для сервера ![NSLookup](media/ad-fs-tshoot-dns/dns2.png)

## <a name="tracert"></a>Tracert
Определяет путь к месту назначения, по отправку сообщений протокола ICMP (Internet Control) эхо-запрос или ICMPv6-сообщения в место назначения с постоянным увеличением срока жизни (TTL) значений полей.   Дополнительные сведения см. в разделе [Tracert](https://technet.microsoft.com/library/ff961507.aspx).


### <a name="to-use-tracert"></a>Чтобы использовать команду Tracert
1.  Откройте командную строку
2. Введите команду tracert <name of adfs server> . Пример: tracert sts.contoso.com
3. Вы должны увидеть конечный путь, используемый для доступа к серверу ![Tracert](media/ad-fs-tshoot-dns/dns3.png)

## <a name="next-steps"></a>Следующие шаги

- [Устранение неполадок AD FS](ad-fs-tshoot-overview.md)