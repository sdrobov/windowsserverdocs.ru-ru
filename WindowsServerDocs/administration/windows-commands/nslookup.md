---
title: nslookup
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 41516932-7833-434a-aa92-b4cf0f9a7ef7
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 84e3e9ee920f458ca775dd7b76d892f10ba2f992
ms.sourcegitcommit: ee8e0b217be6f6b2532ee7265fb4be00c106e124
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70878113"
---
# <a name="nslookup"></a>nslookup

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает сведения, которые можно использовать для диагностики инфраструктуры системы доменных имен (DNS). Перед использованием этого средства необходимо ознакомиться с принципами работы DNS. Программа командной строки Nslookup доступна, только если установлен протокол TCP/IP.
## <a name="syntax"></a>Синтаксис

```
nslookup [<-SubCommand ...>] [{<computerTofind> | -<Server>}]
nslookup /exit
nslookup /finger [<UserName>] [{[>] <FileName>|[>>] <FileName>}]
nslookup /{help | ?}
nslookup /ls [<Option>] <DNSDomain> [{[>] <FileName>|[>>] <FileName>}]
nslookup /lserver <DNSDomain> 
nslookup /root 
nslookup /server <DNSDomain>
nslookup /set <KeyWord>[=<Value>]
nslookup /set all 
nslookup /set class=<Class>
nslookup /set [no]d2
nslookup /set [no]debug
nslookup /set [no]defname
nslookup /set domain=<DomainName>
nslookup /set [no]ignore
nslookup /set port=<Port>
nslookup /set querytype=<ResourceRecordtype>
nslookup /set [no]recurse
nslookup /set retry=<Number>
nslookup /set root=<RootServer>
nslookup /set [no]search
nslookup /set srchlist=<DomainName>[/...]
nslookup /set timeout=<Number>
nslookup /set type=<ResourceRecordtype>
nslookup /set [no]vc
nslookup /view <FileName>
```

## <a name="parameters"></a>Параметры

|                       Параметр                       |                                                                                                         Описание                                                                                                         |
|-------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   [nslookup exit Command](nslookup-exit-command.md)   |                                                                                                     Выход из программы **nslookup**.                                                                                                     |
| [nslookup finger Command](nslookup-finger-command.md) |                                                                                  Подключается к серверу finger на текущем компьютере.                                                                                   |
|           [nslookup help](nslookup-help.md)           |                                                                                    Отображает краткую сводку подкоманд **nslookup** .                                                                                    |
|             [nslookup ls](nslookup-ls.md)             |                                                                                             Выводит сведения для домена DNS.                                                                                             |
|        [nslookup lserver](nslookup-lserver.md)        |                                                                                   Изменяет сервер по умолчанию на указанный домен DNS.                                                                                   |
|           [nslookup root](nslookup-root.md)           |                                                                     Изменяет сервер по умолчанию на сервер для корня пространства имен домена DNS.                                                                     |
|         [nslookup server](nslookup-server.md)         |                                                                                   Изменяет сервер по умолчанию на указанный домен DNS.                                                                                   |
|            [nslookup set](nslookup-set.md)            |                                                                              Изменяет параметры конфигурации, влияющие на работу функций Lookup.                                                                               |
|        [nslookup set all](nslookup-set-all.md)        |                                                                                  Выводит текущие значения параметров конфигурации.                                                                                   |
|      [nslookup set class](nslookup-set-class.md)      |                                                                     Изменяет класс запроса. Класс указывает группу протоколов сведений.                                                                     |
|         [nslookup set d2](nslookup-set-d2.md)         |                                                                     Включает или выключает режим полной отладки. Выводятся все поля каждого пакета.                                                                      |
|      [nslookup set debug](nslookup-set-debug.md)      |                                                                                               Включает или выключает режим отладки.                                                                                               |
|                 nslookup/set дефнаме                 |                                            Добавляет доменное имя DNS по умолчанию в запрос поиска одного компонента. Один компонент — это компонент, который не содержит точек.                                            |
|     [nslookup set domain](nslookup-set-domain.md)     |                                                                                 Изменяет имя домена DNS по умолчанию на указанное имя.                                                                                  |
|                 nslookup/set Ignore                  |                                                                                              Игнорирует ошибки усечения пакетов.                                                                                              |
|       [nslookup set port](nslookup-set-port.md)       |                                                                          Изменяет порт сервера DNS-имен TCP/UDP по умолчанию на указанное значение.                                                                           |
|  [nslookup set querytype](nslookup-set-querytype.md)  |                                                                                       Изменяет тип записи ресурса для запроса.                                                                                       |
|    [nslookup set recurse](nslookup-set-recurse.md)    |                                                                    Сообщает серверу DNS-имен о необходимости запрашивать другие серверы, если у него нет сведений.                                                                    |
|      [nslookup set retry](nslookup-set-retry.md)      |                                                                                                 Задает число повторных попыток.                                                                                                 |
|       [nslookup set root](nslookup-set-root.md)       |                                                                                    Изменяет имя корневого сервера, используемого для запросов.                                                                                    |
|     [nslookup set search](nslookup-set-search.md)     | Добавляет DNS-имена доменов в списке поиска доменов DNS в запрос, пока не будет получен ответ. Это применимо, когда набор и запрос уточняющего запроса содержат по крайней мере одну точку, но не заканчиваются точкой в конце. |
|   [nslookup set srchlist](nslookup-set-srchlist.md)   |                                                                                    Изменяет имя домена DNS по умолчанию и список поиска.                                                                                     |
|    [nslookup set timeout](nslookup-set-timeout.md)    |                                                                           Изменяет начальное число секунд ожидания ответа на запрос.                                                                           |
|       [nslookup set type](nslookup-set-type.md)       |                                                                                       Изменяет тип записи ресурса для запроса.                                                                                       |
|         [nslookup set vc](nslookup-set-vc.md)         |                                                                     Указывает, следует ли использовать виртуальный канал при отправке запросов на сервер.                                                                      |
|           [nslookup view](nslookup-view.md)           |                                                                          Сортирует и перечисляет выходные данные предыдущей подкоманды **Ls** или команд.                                                                          |

## <a name="remarks"></a>Примечания
- Если *компутертофинд* является IP-адресом и запрос предназначен для типа записи ресурса A или PTR, возвращается имя компьютера. Если *компутертофинд* является именем и не имеет точки в конце, имя домена DNS по умолчанию добавляется к имени. Это поведение зависит от состояния следующих подкоманд **Set** : **domain**, **срчлист**, **дефнаме**и **Search**.
- Если ввести дефис (-) вместо *компутертофинд*, Командная строка изменится на интерактивный режим **nslookup** .
- Длина командной строки должна быть меньше 256 символов.
- **nslookup** имеет два режима: интерактивный и неинтерактивный.
  Если необходимо выполнить поиск только одного фрагмента данных, используйте Неинтерактивный режим. В качестве первого параметра введите имя или IP-адрес компьютера, который требуется найти. Во втором параметре введите имя или IP-адрес сервера DNS-имен. Если опустить второй аргумент, **nslookup** использует сервер DNS-имен по умолчанию.
  Если необходимо найти более одного фрагмента данных, можно использовать интерактивный режим. Введите дефис (-) для первого параметра, а также имя или IP-адрес сервера DNS-имен для второго параметра. Или опустите оба параметра, и **nslookup** использует сервер DNS по умолчанию. Ниже приведены некоторые советы по работе в интерактивном режиме.
  -   Чтобы прервать Интерактивные команды в любое время, нажмите клавиши CTRL + B.
  -   Для выхода введите **Exit**.
  -   Чтобы интерпретировать встроенную команду как имя компьютера, перед ней следует использовать escape-символ (\\).
  -   Нераспознанная команда интерпретируется как имя компьютера.
- Если запрос на поиск завершается неудачей, **nslookup** выводит сообщение об ошибке. В следующей таблице перечислены возможные сообщения об ошибках.
  |**Сообщение об ошибке**|**Описание**|
  |-----------|----------|
  |`timed out`|Сервер не ответил на запрос по истечении определенного промежутка времени и определенного числа повторных попыток. Время ожидания можно установить с помощью подкоманды **Set timeout** . Число повторных попыток можно задать с помощью подкоманды **set retry** .|
  |`No response from server`|Сервер DNS-имен не работает на компьютере сервера.|
  |`No records`|Сервер DNS-имен не имеет записей ресурсов текущего типа запроса для компьютера, хотя имя компьютера является допустимым. Тип запроса указывается с помощью команды **Set QueryType** .|
  |`Nonexistent domain`|Имя компьютера или домена DNS не существует.|
  |`Connection refused`<br /><br />-или-<br /><br />`Network is unreachable`|Не удалось установить подключение к серверу DNS-имен или серверу finger. Эта ошибка обычно возникает при запросах **Ls** и **finger** .|
  |`Server failure`|Сервер DNS-имен обнаружил внутреннюю несогласованность в своей базе данных и не смог вернуть допустимый ответ.|
  |`Refused`|Серверу DNS-имен отказано в обслуживании запроса.|
  |`format error`|Сервер DNS-имен обнаружил, что пакет запроса имеет неправильный формат. Это может указывать на ошибку в **nslookup**.|
- Дополнительные сведения о команде **nslookup** и DNS см. в следующих ресурсах:
  - Иванов, T., Дэвиса, J. 2000. *Технический справочник по протоколам и службам TCP/IP Microsoft Windows 2000*. Redmond, штат Вашингтон: Microsoft Press.
  - Албитз, P., Лаукидес, M. и C. Лю. 2001. *DNS и BIND, четвертый выпуск*. Себастопол, штат Калифорния: O'Reilly и Associates, Inc.
  - Ларсон (, M. и C. Лю. 2001. *DNS в Windows 2000*. Себастопол, штат Калифорния: O'Reilly и Associates, Inc.
    #### <a name="examples"></a>Примеры
    Каждый параметр командной строки состоит из дефиса (-), за которым следует имя команды, а в некоторых случаях — знак равенства (=) и значение. Например, чтобы изменить тип запроса по умолчанию на сведения о хосте (компьютере), а исходное время ожидания — на 10 секунд, введите команду **nslookup-QueryType = HINFO-timeout = 10** .
    ## <a name="see-also"></a>См. также
    [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
