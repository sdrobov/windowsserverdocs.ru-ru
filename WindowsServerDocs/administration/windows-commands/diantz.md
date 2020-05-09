---
title: diantz
description: Справочный раздел по команде диантз, которая упаковывает существующие файлы в CAB-файл.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 218ed5d7-1203-4d68-ad9b-65cdd022d54f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e45c0c4f71bc7faf6d5de0fa198ac872f6ff2597
ms.sourcegitcommit: fad2ba64bbc13763772e21ed3eabd010f6a5da34
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2020
ms.locfileid: "82992500"
---
# <a name="diantz"></a>diantz

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Упакуйте существующие файлы в CAB-файл. Эта команда выполняет те же действия, что и обновленная [команда makecab](makecab.md).

## <a name="syntax"></a>Синтаксис

```
diantz [/v[n]] [/d var=<value> ...] [/l <dir>] <source> [<destination>]
diantz [/v[<n>]] [/d var=<value> ...] /f <directives_file> [...]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<source>` | Файл для сжатия. |
| `<destination>` | Имя файла для предоставления сжатого файла. Если этот параметр опущен, последний символ имени исходного файла заменяется символом подчеркивания (_) и используется в качестве назначения. |
| /f `<directives_file>` | Файл с директивами **диантз** (может повторяться). |
| /d var =`<value>` | Определяет переменную с указанным значением. |
| /l`<dir>` | Расположение для размещения назначения (по умолчанию текущий каталог). |
| /v [`<n>`] | Задать уровень детализации отладки (0 = нет,..., 3 = полный). |
| /? | Отображение справки в командной строке. |

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Формат CAB-файла Microsoft](https://docs.microsoft.com/previous-versions/bb417343(v=msdn.10))
