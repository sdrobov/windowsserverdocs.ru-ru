---
title: makecab
description: Справочный раздел по команде makecab, которая упаковывает существующие файлы в CAB-файл.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4da95297-c593-427b-9f76-2f389c46cbf4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 192471e6045a530e9deedec70cc957b9362b3ae7
ms.sourcegitcommit: 5e313a004663adb54c90962cfdad9ae889246151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84354664"
---
# <a name="makecab"></a>makecab

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Упакуйте существующие файлы в CAB-файл.


> [!NOTE]
> Эта команда аналогична [команде диантз](diantz.md).

## <a name="syntax"></a>Синтаксис

```
makecab [/v[n]] [/d var=<value> ...] [/l <dir>] <source> [<destination>]
makecab [/v[<n>]] [/d var=<value> ...] /f <directives_file> [...]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<source>` | Файл для сжатия. |
| `<destination>` | Имя файла для предоставления сжатого файла. Если этот параметр опущен, последний символ имени исходного файла заменяется символом подчеркивания (_) и используется в качестве назначения. |
| /f `<directives_file>` | Файл с директивами **makecab** (может повторяться). |
| /d var =`<value>` | Определяет переменную с указанным значением. |
| /l`<dir>` | Расположение для размещения назначения (по умолчанию текущий каталог). |
| /v [ `<n>` ] | Задать уровень детализации отладки (0 = нет,..., 3 = полный). |
| /? | Отображение справки в командной строке. |

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда диантз](diantz.md)

- [Формат CAB-файла Microsoft](https://docs.microsoft.com/previous-versions/bb417343(v=msdn.10))
