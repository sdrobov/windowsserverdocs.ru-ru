---
title: Set-TransportServer подкоманды
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7863225c-f4b2-4cd0-b929-78a454bef249
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d144ed7d461cbebcd351aa4347fde20f35736c26
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59886605"
---
# <a name="subcommand-set-transportserver"></a>Подкоманда: set-TransportServer

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Задает параметры конфигурации для транспортного сервера.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Set-TransportServer [/Server:<Server name>]
     [/ObtainIpv4From:{Dhcp | Range}]
        [/start:<starting IP address>]
        [/End:<Ending IP address>]
     [/ObtainIpv6From:Range]\n\
        [/start:<start IP address>]\n\
        [/End:<End IP address>]      
     [/startPort:<starting port>
        [/EndPort:<starting port>
     [/Profile:{10Mbps | 100Mbps | 1Gbps | Custom}]    
     [/MulticastSessionPolicy]
             [/Policy:{None | AutoDisconnect | Multistream}]
                 [/Threshold:<Speed in KBps>]
                 [/StreamCount:{2 | 3}]
                 [/Fallback:{Yes | No}]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/ Server:<Server name>]|Задает имя используемого транспортного сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя транспортного сервера не указано, используется локальный сервер.|
|[/ObtainIpv4From:{Dhcp &#124; Range}]|Задает источник IPv4-адреса следующим образом:<br /><br />-[/ start: <IP address>] Задает начало диапазона IP-адресов. Это необходимо, и допустимым, только если этот параметр имеет значение **диапазон**.<br />-[/ End: <IP address>] Задает конец диапазона IP-адресов. Это необходимо, и допустимым, только если этот параметр имеет значение **диапазон**.<br />-[/ значение startPort: <port>] Задает начало диапазона портов.<br />-[/ Значения EndPort: <port>] Задает конец диапазона портов.|
|[/ ObtainIpv6From:Range]|Указывает источник IPv6-адресов. Этот параметр применяется только к Windows Server 2008 R2 и единственным поддерживаемым значением является **диапазон**.<br /><br />-[/ start: <IP address>] Задает начало диапазона IP-адресов. Это необходимо, и допустимым, только если этот параметр имеет значение **диапазон**.<br />-[/ End: <IP address>] Задает конец диапазона IP-адресов. Это необходимо, и допустимым, только если этот параметр имеет значение **диапазон**.<br />-[/ значение startPort: <port>] Задает начало диапазона портов.<br />-[/ Значения EndPort: <port>] Задает конец диапазона портов.|
|[/ Profile: {10 Мбит/с &#124; 100 Мбит/с &#124; 1 Гбит/с &#124; Custom}]|Указывает сетевой профиль для использования. Этот параметр доступен только для серверов под управлением Windows Server 2008 или Windows Server 2003.|
|[/MulticastSessionPolicy]|Настройка параметров передачи процесса многоадресной передачи. Эта команда доступна только для Windows Server 2008 R2.<br /><br />-[/ Политики: {None &#124; автоматического отключения &#124; Multistream}] определяет способ обработки медленных клиентов. **Нет** означает, что для сохранения всех клиентов в одном сеансе с той же скоростью. **Автоматического отключения** означает, что все клиенты, опустится ниже указанного **/Threshold** будут отключены. **Multistream** означает, что клиенты будут разделены на несколько сеансов, в соответствии с **/StreamCount**.<br />-[/ Пороговое значение:<Speed in KBps>] Задает минимальную скорость передачи в Кбит/с для **/Policy:AutoDisconnect**. Клиенты, которые опустится ниже эта скорость отключаются от многоадресные передачи.<br />-[/ StreamCount: {2 &#124; 3}] [/ резервный: {Да &#124; No}] определяет количество сеансов для **/Policy:Multistream**. **2** означает, что два сеанса (быстрых и медленных запросов) и **3** означает трех сеансов (медленно, средний, быстро).<br />-[/ Резервный: {Да &#124; No}] определяет ли отключены tha клиентов будет продолжить перенос с помощью другого метода (если поддерживается клиентом). Если вы используете клиент WDS, компьютер возвращается к одноадресную. Wdsmcast.exe не поддерживает резервный механизм. Этот параметр также применяется к клиентам, не поддерживают **Multistream**. В этом случае компьютер вернется к другой метод вместо перемещения медленнее сеанса передачи.|
## <a name="BKMK_examples"></a>Примеры
Чтобы задать диапазон IPv4-адресов для сервера, введите следующую команду:
```
wdsutil /Set-TransportServer /ObtainIpv4From:Range /start:239.0.0.1 /End:239.0.0.100
```
Чтобы задать диапазон адресов IPv4, диапазон портов и профиль для сервера, введите следующую команду:
```
wdsutil /Set-TransportServer /Server:MyWDSServer /ObtainIpv4From:Range /start:239.0.0.1 /End:239.0.0.100 /startPort:12000 /EndPort:50000 /Profile:10mbps
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды disable-TransportServer](using-the-disable-transportserver-command.md)
[с помощью команды enable-TransportServer](using-the-enable-transportserver-command.md) 
 [ С помощью команды get-TransportServer](using-the-get-transportserver-command.md)
[подкоманда: start-TransportServer](subcommand-start-transportserver.md)
[подкоманда: stop-TransportServer](subcommand-stop-transportserver.md)
