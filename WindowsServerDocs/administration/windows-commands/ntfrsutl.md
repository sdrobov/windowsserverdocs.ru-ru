---
title: ntfrsutl
description: Справочная статья по команде нтфрсутл, которая выводит сведения о внутренних таблицах, потоках и памяти для службы репликации файлов NT (NTFRS).
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d7721a19-5a87-4ab6-b816-65d2da2c811f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 56aefc1277f67dc6a06ba4686c26f81592afc2f3
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85925331"
---
# <a name="ntfrsutl"></a>ntfrsutl

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Выводит сведения о внутренних таблицах, потоках и памяти для службы репликации файлов NT (NTFRS) как с локального, так и с удаленного сервера. Параметр восстановления NTFRS в диспетчере управления службами (SCM) может быть критически важным для поиска и хранения важных событий журнала на компьютере. Это средство предоставляет удобный способ проверки этих параметров.

## <a name="syntax"></a>Синтаксис

```
ntfrsutl[idtable|configtable|inlog|outlog][<computer>]
ntfrsutl[memory|threads|stage][<computer>]
ntfrsutl ds[<computer>]
ntfrsutl [sets][<computer>]
ntfrsutl [version][<computer>]
ntfrsutl poll[/quickly[=[<n>]]][/slowly[=[<n>]]][/now][<computer>]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| идтабле | Указывает таблицу ИДЕНТИФИКАТОРов. |
| конфигтабле | Указывает таблицу конфигурации FRS. |
| инлог | Указывает входящий журнал. |
| аутлог | Указывает исходящий журнал. |
| `<computer>` | Указывает компьютер. |
| memory. | Указывает использование памяти. |
| потоки | Указывает использование памяти. |
| разместить | Указывает использование памяти. |
| ds | Перечисление представления службы NTFRS в службе каталогов. |
| наборы | Указывает активные наборы реплик. |
| version | Указывает версии API и службы NTFRS. |
| завершает | Задает текущие интервалы опроса.<ul><li>`/quickly`— Выполняет опросы быстро, пока не будет получено стабильной конфигурации.</li><li>`/quickly=`— Опрашивается каждые количество минут по умолчанию.</li><li>`/quickly=<n>`— Опросы быстро запрашиваются каждые *n* минут.</li><li>`/slowly`— Опрашивается медленно, пока не будет извлечена стабильная конфигурация.</li><li>`/slowly=`— Опрашивается медленно каждое заданное по умолчанию количество минут.</li><li>`/slowly=<n>`— Опрашивается медленнее каждые *n* минут.</li><li>`/now`— Опрашивается сейчас.</li></ul>|
| /? | Отображение справки в командной строке. |

### <a name="examples"></a>Примеры

Чтобы определить интервал опроса для репликации файлов, введите:

```
C:\Program Files\SupportTools>ntfrsutl poll wrkstn-1
```

Чтобы определить текущую версию интерфейса прикладных программ (API) NTFRS, введите:

```
C:\Program Files\SupportTools>ntfrsutl version
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
