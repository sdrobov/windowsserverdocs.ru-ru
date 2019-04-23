---
title: telnet
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b70a6156-9413-4300-84ce-a34c467e2b4e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6439a91d82d6d199666629e333d8130bf65a384b
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59858565"
---
# <a name="telnet"></a>telnet

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Взаимодействует с компьютера под управлением службы сервера telnet. 
## <a name="syntax"></a>Синтаксис
```
telnet [/a] [/e <EscapeChar>] [/f <FileName>] [/l <UserName>] [/t {vt100 | vt52 | ansi | vtnt}] [<Host> [<Port>]] [/?]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/a|Попытка автоматического входа. Так же, как /l параметр за исключением использует пользователя по имени пользователя s.|
|/e \<EscapeChar>|Escape-символ, используемый для ввода строки клиента telnet.|
|/f \<имя файла >|Имя файла, используемые для ведения журнала на стороне клиента.|
|/l \<имя пользователя >|Указывает имя пользователя для входа в систему на удаленном компьютере.|
|/t {vt100 &#124; vt52 &#124; ansi &#124; vtnt}|Указывает тип терминала. Поддерживаемые типы терминалов: vt100, vt52, ansi и vtnt.|
|\<Узел > [\<порт >]|Указывает имя узла или IP-адрес удаленного компьютера для подключения к и при необходимости использовать TCP-порт (по умолчанию — TCP-порт 23).|
|/?|Отображение справки в командной строке. Кроме того можно ввести /h.|

## <a name="remarks"></a>Примечания
-   Перед выполнением этой команды необходимо установить программное обеспечение клиента telnet. Дополнительные сведения см. в разделе [Установка telnet](https://technet.microsoft.com/library/cc754293(v=ws.10).aspx).
-   Можно запустить telnet без параметров, входят в контекст telnet, указано в строке telnet (**Microsoft telnet >**). В командной строке telnet можно использовать команды telnet для управления компьютером под управлением клиента telnet.

## <a name="BKMK_Examples"></a>Примеры
Для подключения к компьютеру под управлением службы сервера telnet в telnet.microsoft.com используйте telnet.
```
telnet telnet.microsoft.com
```
Используйте telnet, чтобы подключиться к компьютеру под управлением службы сервера telnet в telnet.microsoft.com через TCP-порт 44 и журнала активности сеанса в локальный файл с именем telnetlog.txt
```
telnet /f telnetlog.txt telnet.microsoft.com 44
```

## <a name="additional-references"></a>Дополнительные ссылки
-   [Установка telnet](https://technet.microsoft.com/library/cc754293(v=ws.10).aspx)
-   [Технический справочник по Telnet](https://technet.microsoft.com/library/cc754987(v=ws.10).aspx)
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)
