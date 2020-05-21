---
title: exec
description: Справочный раздел для команды EXEC, которая запускает файл скрипта на локальном компьютере.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 364e8baf-576f-401b-a431-7d3c06621614
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 956f3d4a7c5992980aea0fc0f5933ee7def48381
ms.sourcegitcommit: bf887504703337f8ad685d778124f65fe8c3dc13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2020
ms.locfileid: "83436110"
---
# <a name="exec"></a>exec

Запускает файл скрипта на локальном компьютере. Эта команда также дублирует или восстанавливает данные в рамках последовательности резервного копирования или восстановления. В случае сбоя скрипта возвращается ошибка, и сценарий DiskShadow завершает работу.

Файл может быть сценарием **cmd** .

## <a name="syntax"></a>Синтаксис

```
exec <scriptfile.cmd>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<scriptfile.cmd>` | Указывает запускаемый файл скрипта. |

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Diskshadow, команда](diskshadow.md)
