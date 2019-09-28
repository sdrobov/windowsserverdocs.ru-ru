---
title: Набор подкоманд-Транспортсервер
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: f91cca044d4c2922791ccb63b0e3cec4af685f17
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71370742"
---
# <a name="subcommand-set-transportserver"></a>Подкоманда: Set-Транспортсервер

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

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
|[/Server: <Server name>]|Указывает имя транспортного сервера. Это может быть NetBIOS-имя или полное доменное имя (FQDN). Если имя транспортного сервера не указано, используется локальный сервер.|
|[/ObtainIpv4From: {диапазон &#124; DHCP}]|Задает источник IPv4-адресов следующим образом:<br /><br />-[/Start: <IP address>] задает начало диапазона IP-адресов. Этот параметр является обязательным и допустимым, только если для этого параметра задано значение **Range**.<br />-[/Енд: <IP address>] задает конец диапазона IP-адресов. Этот параметр является обязательным и допустимым, только если для этого параметра задано значение **Range**.<br />-[/Стартпорт: <port>] задает начало диапазона портов.<br />-[/Ендпорт: <port>] задает конец диапазона портов.|
|[/ObtainIpv6From: Range]|Указывает источник IPv6-адресов. Этот параметр применяется только к Windows Server 2008 R2, а единственное поддерживаемое значение — **Range**.<br /><br />-[/Start: <IP address>] задает начало диапазона IP-адресов. Этот параметр является обязательным и допустимым, только если для этого параметра задано значение **Range**.<br />-[/Енд: <IP address>] задает конец диапазона IP-адресов. Этот параметр является обязательным и допустимым, только если для этого параметра задано значение **Range**.<br />-[/Стартпорт: <port>] задает начало диапазона портов.<br />-[/Ендпорт: <port>] задает конец диапазона портов.|
|[/Profile: {10 &#124; Мбит &#124; / &#124; с, 1Gbps настраиваемый}]|Указывает используемый сетевой профиль. Этот параметр доступен только для серверов под Windows Server 2008 или Windows Server 2003.|
|[/Мултикастсессионполици]|Настраивает параметры передачи для многоадресных передач. Эта команда доступна только для Windows Server 2008 R2.<br /><br />-[/Полици: {None &#124; Автоотключение &#124; многопотоковой передачи}] определяет способ обработки замедляют клиентов. **None** означает, что все клиенты должны находиться в одном сеансе с одинаковой скоростью. Автоматическое **Отключение** означает, что все клиенты, которые удаляются ниже указанного **/срешолд** , отключаются. **Многопотоковая передача** означает, что клиенты будут разделены на несколько сеансов, как указано в **/стреамкаунт**.<br />-[/Срешолд: <Speed in KBps>] задает минимальную скорость передачи в кбит/с для **/полици: Автоотключение**. Клиенты, которые отменяют эту частоту, отключаются от многоадресных передач.<br />-[/Стреамкаунт: {2 &#124; 3}] [/фаллбакк: {Да &#124; }] определяет число сеансов для **/полици: "многопотоковый**". **2** означает два сеанса (быстрый и медленный), а **3** — три сеанса (медленный, средний, быстрый).<br />-[/Фаллбакк: {Yes &#124; }] определяет, будут ли клиенты, Tha, отключены, продолжать перенос с помощью другого метода (если он поддерживается клиентом). Если вы используете WDS-клиент, компьютер будет возвращаться к одноадресной рассылке. Wdsmcast. exe не поддерживает резервный механизм. Этот параметр также применяется к клиентам, которые не поддерживают **многопотоковую передачу**. В этом случае компьютер будет возвращаться к другому методу, а не к более медленному сеансу передачи.|
## <a name="BKMK_examples"></a>Примеров
Чтобы задать диапазон IPv4-адресов для сервера, введите:
```
wdsutil /Set-TransportServer /ObtainIpv4From:Range /start:239.0.0.1 /End:239.0.0.100
```
Чтобы задать диапазон IPv4-адресов, диапазон портов и профиль для сервера, введите:
```
wdsutil /Set-TransportServer /Server:MyWDSServer /ObtainIpv4From:Range /start:239.0.0.1 /End:239.0.0.100 /startPort:12000 /EndPort:50000 /Profile:10mbps
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды disable-транспортсервер](using-the-disable-transportserver-command.md)
[с помощью команды Enable-Транспортсервер](using-the-enable-transportserver-command.md)
[с помощью команды Get-транспортсервер](using-the-get-transportserver-command.md)
[. подкоманда Start-Транспортсервер](subcommand-start-transportserver.md)
[: останавливается-транспортсервер](subcommand-stop-transportserver.md)
