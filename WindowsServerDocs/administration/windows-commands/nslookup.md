---
title: nslookup
description: 'Раздел Windows команды для ***- '
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
ms.openlocfilehash: b3c20855befbe71413fa8fdb44925b8b634c0c11
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59841655"
---
# <a name="nslookup"></a>nslookup

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает сведения, которые можно использовать для диагностики инфраструктуры доменных имен (DNS). Прежде чем использовать это средство, необходимо ознакомиться с принципами работы DNS. Средство командной строки nslookup доступна только в том случае, если вы установили протокола TCP/IP.
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
|Параметр|Описание|
|-------|--------|
|[Nslookup выхода команды](nslookup-exit-command.md)|завершает работу **nslookup**.|
|[Nslookup палец команды](nslookup-finger-command.md)|Подключается к серверу finger на текущем компьютере.|
|[Nslookup справки](nslookup-help.md)|Отображает краткое описание **nslookup** подкоманды.|
|[nslookup ls](nslookup-ls.md)|Выводит сведения для домена DNS.|
|[Nslookup lserver](nslookup-lserver.md)|Изменение сервера по умолчанию для указанного домена DNS.|
|[корневой nslookup](nslookup-root.md)|Изменение сервера по умолчанию на сервер для корня пространства имен доменов DNS.|
|[nslookup server](nslookup-server.md)|Изменение сервера по умолчанию для указанного домена DNS.|
|[набор nslookup](nslookup-set.md)|Изменяет параметры конфигурации, которые влияют на том, как функция уточняющих запросов.|
|[Nslookup, установить все](nslookup-set-all.md)|Выводит текущие значения параметров конфигурации.|
|[Класс set nslookup](nslookup-set-class.md)|изменяет класс запроса. Класс определяет группу протоколов информации.|
|[nslookup set d2](nslookup-set-d2.md)|Включает углубленный режим отладки, включить или отключить. Выводятся все поля каждого пакета.|
|[значение параметра debug nslookup](nslookup-set-debug.md)|Включает режим отладки, включить или отключить.|
|nslookup/set defname|Добавляет DNS-имя домена по умолчанию запрос поиска одного компонента. Один компонент является компонентом, не содержащий точек.|
|[Nslookup задайте домен](nslookup-set-domain.md)|Изменяет имя домена DNS по умолчанию к имени, указанному.|
|игнорировать/Set nslookup|Игнорирует ошибки усечения пакетов.|
|[Nslookup задать номер порта](nslookup-set-port.md)|Изменение порта сервера имен DNS TCP/UDP на указанное значение.|
|[nslookup set querytype](nslookup-set-querytype.md)|Изменяет тип записи ресурса для запроса.|
|[recurse набора nslookup](nslookup-set-recurse.md)|Указывает, что сервер имя DNS для запроса других серверов, если он не содержит данные.|
|[Nslookup набор повтора](nslookup-set-retry.md)|Задает число повторных попыток.|
|[Nslookup задать корень](nslookup-set-root.md)|Изменяет имя корневого сервера, используемого для запросов.|
|[Поиск набора nslookup](nslookup-set-search.md)|Добавляет к запросу доменных имен DNS в список поиска DNS домена, пока не будет получен ответ. Это применимо, когда набор и поиска запросов, содержать по крайней мере одну точку, но не заканчиваться точку.|
|[nslookup set srchlist используется](nslookup-set-srchlist.md)|изменяет список по умолчанию DNS домена и имя.|
|[задать время ожидания nslookup](nslookup-set-timeout.md)|Изменяет начальное количество секунд ожидания ответа на запрос.|
|[Тип набора nslookup](nslookup-set-type.md)|Изменяет тип записи ресурса для запроса.|
|[nslookup set vc](nslookup-set-vc.md)|Указывает, использовать или не использовать виртуальный канал при отправке запросов к серверу.|
|[представление nslookup](nslookup-view.md)|Сортирует и вывод предыдущего **ls** подкоманд и команд.|
## <a name="remarks"></a>Примечания
-   Если *Искомый_компьютер* является IP-адресом и запрашивается объект или возвращается PTR тип записи ресурса, имя компьютера. Если *Искомый_компьютер* — это имя и не содержит символ период по умолчанию к имени добавляется имя домена DNS. Это поведение зависит от состояния из следующих **задать** подкоманды: **домена**, **srchlist используется**, **defname**, и  **Поиск**.
-   При вводе дефиса (-) вместо *Искомый_компьютер*, командной строки изменяется на **nslookup** интерактивный режим.
-   Длина командной строки должна быть меньше 256 символов.
-   **Nslookup** имеет два режима: интерактивном и автономном.
    Если необходимо выполнить поиск только одного набора данных, используйте обычный режим. Для первого параметра введите имя или IP-адрес компьютера, на котором вы хотите найти. Для второго параметра введите имя или IP-адрес DNS-имя сервера. Если не указан второй аргумент, **nslookup** использует DNS-имя сервера по умолчанию.
    Если вам нужно найти более одного блока данных, можно использовать интерактивный режим. Введите дефис (-) для первого параметра, имя и IP-адрес DNS-имя сервера для второго параметра. Или, если не заданы оба параметра и **nslookup** использует DNS-имя сервера по умолчанию. Ниже приведены некоторые советы по работе в интерактивном режиме.
    -   Чтобы прервать интерактивных команд в любое время, нажмите клавиши CTRL + B.
    -   Чтобы выйти, введите **выйти из**.
    -   Следует считать имя компьютера является встроенной командой, поставили escape-символ (\\).
    -   Нераспознанная команда интерпретируется как имя компьютера.
-   в случае сбоя запрос на поиск **nslookup** выводится сообщение об ошибке. В следующей таблице перечислены возможные сообщения об ошибке.
    |**Сообщение об ошибке**|**Описание**|
    |-----------|----------|
    |`timed out`|Сервер не ответил на запрос после определенное количество времени и определенного числа повторных попыток. Можно задать период ожидания с **задать время ожидания** подкоманды. Можно задать количество повторных попыток с **повтора набора** подкоманды.|
    |`No response from server`|Имя DNS-сервер выполняется на компьютере сервера.|
    |`No records`|Имя DNS-сервер не поддерживает записи ресурсов текущего типа запроса для компьютера, несмотря на то, что имя компьютера является допустимым. Тип запроса указывается с помощью **задать querytype** команды.|
    |`Nonexistent domain`|Компьютер или DNS-имя домена не существует.|
    |`Connection refused`<br /><br />-или-<br /><br />`Network is unreachable`|Не удалось установить подключение к DNS-имя сервера или сервера палец. Эта ошибка обычно возникает с **ls** и **палец** запросов.|
    |`Server failure`|Имя DNS-сервер обнаружил внутреннее несоответствие в своей базе данных и не может неправильно.|
    |`Refused`|Имя DNS-сервер отказался обслуживания запроса.|
    |`format error`|Имя DNS-сервер найден, что пакета запроса не был в неправильном формате. Это может свидетельствовать об ошибке в **nslookup**.|
-   Дополнительные сведения о **nslookup** команды и DNS, ознакомьтесь со следующими ресурсами:
    -   Lee, T., Дэвис, J. 2000. *Технический справочник по Microsoft Windows 2000 TCP/IP Protocols and Services*. Редмонд, штат Вашингтон: Microsoft Press.
    -   Albitz M. P. Loukides и C. лю. 2001. *DNS и BIND, четвертый выпуск*. Sebastopol, шт. Калифорния: O'Reilly and associates, Inc.
    -   Larson M. и C. лю. 2001. *DNS в Windows 2000*. Sebastopol, шт. Калифорния: O'Reilly and associates, Inc.
#### <a name="examples"></a>Примеры
Каждый параметр состоит из дефиса (-), за которым следует название команды и в некоторых случаях, знака равенства (=) и значение. Например, чтобы изменить тип запроса по умолчанию на сведения об узле (компьютер) и начальное время ожидания 10 секунд, введите: **nslookup - querytype = hinfo - timeout = 10**
## <a name="see-also"></a>См. также
[Ключ синтаксиса командной строки](command-line-syntax-key.md)
