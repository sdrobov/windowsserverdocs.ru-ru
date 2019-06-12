---
title: makecab
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4da95297-c593-427b-9f76-2f389c46cbf4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7b120cf990abe2024fd6c96ca2f1ef11fa2350ae
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66437529"
---
# <a name="makecab"></a>makecab

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Упакуйте существующие файлы в CAB-файл.
## <a name="syntax"></a>Синтаксис
```
makecab [/v[n]] [/d var=<value> ...] [/l <dir>] <source> [<destination>]
makecab [/v[<n>]] [/d var=<value> ...] /f <directives_file> [...]
```
### <a name="parameters"></a>Параметры

|      Параметр       |                                                                        Описание                                                                        |
|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
|       <source>       |                                                                     Файл для сжатия.                                                                     |
|    <destination>     | Имя файла, чтобы предоставить сжатого файла. Если этот параметр опущен, последнего символа имени исходного файла заменен символом подчеркивания (_) и использовать в качестве назначения. |
| /f < directives_file > |                                                   Файл с **makecab** директивы (повторно).                                                   |
|    /d var =<value>    |                                                          Определяет переменную с указанным значением.                                                           |
|       /l <dir>       |                                               Расположение назначения (по умолчанию — текущий каталог).                                               |
|       /v[<n>]        |                                                    Задайте уровень детализации отладки (0 = нет,..., 3 = полный).                                                     |
|          /?          |                                                           Отображение справки в командной строке.                                                            |

## <a name="remarks"></a>Примечания
-   Ссылаться на [формата CAB-файл Microsoft](https://go.microsoft.com/fwlink/?LinkId=226852) на сайте MSDN, сведения о directive_file.

## <a name="additional-references"></a>Дополнительные ссылки
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

