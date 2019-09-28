---
title: makecab
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: b0231b6f1ddd3e81caa7544587f764e2308015b8
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71374154"
---
# <a name="makecab"></a>makecab

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

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
|    <destination>     | Имя файла для предоставления сжатого файла. Если этот параметр опущен, последний символ имени исходного файла заменяется символом подчеркивания (_) и используется в качестве назначения. |
| /f < directives_file > |                                                   Файл с директивами **makecab** (может повторяться).                                                   |
|    /d var =<value>    |                                                          Определяет переменную с указанным значением.                                                           |
|       /l <dir>       |                                               Расположение для размещения назначения (по умолчанию текущий каталог).                                               |
|       /v [<n>]        |                                                    Задать уровень детализации отладки (0 = нет,..., 3 = полный).                                                     |
|          /?          |                                                           Отображение справки в командной строке.                                                            |

## <a name="remarks"></a>Примечания
-   Сведения о directive_file см. в [формате CAB-файла Майкрософт](https://go.microsoft.com/fwlink/?LinkId=226852) на сайте MSDN.

## <a name="additional-references"></a>Дополнительные ссылки
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

