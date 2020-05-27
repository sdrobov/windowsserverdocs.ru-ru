---
title: telnet
description: Справочный раздел по Telnet, который взаимодействует с компьютером, на котором работает служба Telnet-сервера.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b70a6156-9413-4300-84ce-a34c467e2b4e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c1718d1d74849949769d4d8fffbf3d93cc088742
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83821034"
---
# <a name="telnet"></a>telnet

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Взаимодействует с компьютером, на котором запущена служба Telnet-сервера.

## <a name="syntax"></a>Синтаксис
```
telnet [/a] [/e <EscapeChar>] [/f <FileName>] [/l <UserName>] [/t {vt100 | vt52 | ansi | vtnt}] [<Host> [<Port>]] [/?]
```
#### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/a|попытка автоматического входа в систему. То же, что и параметр/l, за исключением использования имени пользователя, выполнившего вход в систему.|
|/e \< EscapeChar>|Escape-символ, используемый для ввода запроса клиента Telnet.|
|/f \< имя файла>|Имя файла, используемое для ведения журнала на стороне клиента.|
|/l \< имя пользователя>|Указывает имя пользователя для входа на удаленный компьютер.|
|/t {VT100 &#124; VT52 &#124; ANSI &#124; VTNT}|Указывает тип терминала. Поддерживаются следующие типы терминалов: VT100, VT52, ANSI и VTNT.|
|\<> узла [ \< порт>]|Указывает имя узла или IP-адрес удаленного компьютера, к которому необходимо подключиться, и при необходимости используемый TCP-порт (по умолчанию это TCP-порт 23).|
|/?|Отображение справки в командной строке. Кроме того, можно ввести/х.|

## <a name="remarks"></a>Замечания
-   Для выполнения этой команды необходимо установить клиентское программное обеспечение Telnet. Дополнительные сведения см. в разделе [Установка Telnet](https://technet.microsoft.com/library/cc754293(v=ws.10).aspx).
-   Можно запустить Telnet без параметров, чтобы ввести контекст Telnet, указанный в командной строке Telnet (**Microsoft telnet>**). В командной строке Telnet можно использовать команды Telnet для управления компьютером, на котором выполняется клиент Telnet.

## <a name="examples"></a>Примеры
Используйте Telnet для подключения к компьютеру, на котором запущена служба сервера Telnet по адресу telnet.microsoft.com.
```
telnet telnet.microsoft.com
```
Используйте Telnet для подключения к компьютеру, на котором выполняется служба Telnet-сервера по адресу telnet.microsoft.com на TCP-порте 44, и заносите активность сеанса в локальный файл с именем телнетлог. txt.
```
telnet /f telnetlog.txt telnet.microsoft.com 44
```

## <a name="additional-references"></a>Дополнительные ссылки
-   [Установка Telnet](https://technet.microsoft.com/library/cc754293(v=ws.10).aspx)
-   [Технический справочник по Telnet](https://technet.microsoft.com/library/cc754987(v=ws.10).aspx)
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
