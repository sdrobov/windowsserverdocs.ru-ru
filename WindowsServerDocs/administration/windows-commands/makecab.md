---
title: makecab
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4da95297-c593-427b-9f76-2f389c46cbf4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 46efbae1d59a85071622df51fc018d0bf73dc504
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80840267"
---
# <a name="makecab"></a>makecab

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Упакуйте существующие файлы в CAB-файл.
## <a name="syntax"></a>Синтаксис
```
makecab [/v[n]] [/d var=<value> ...] [/l <dir>] <source> [<destination>]
makecab [/v[<n>]] [/d var=<value> ...] /f <directives_file> [...]
```
#### <a name="parameters"></a>Параметры

|      Параметр       |                                                                        Описание                                                                        |
|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
|       <source>       |                                                                     Файл для сжатия.                                                                     |
|    <destination>     | Имя файла для предоставления сжатого файла. Если этот параметр опущен, последний символ имени исходного файла заменяется символом подчеркивания (_) и используется в качестве назначения. |
| /f < directives_file > |                                                   Файл с директивами **makecab** (может повторяться).                                                   |
|    /d var =<value>    |                                                          Определяет переменную с указанным значением.                                                           |
|       /l <dir>       |                                               Расположение для размещения назначения (по умолчанию текущий каталог).                                               |
|       /v [<n>]        |                                                    Задать уровень детализации отладки (0 = нет,..., 3 = полный).                                                     |
|          /?          |                                                           Отображает справку в командной строке.                                                            |

## <a name="remarks"></a>Примечания
-   Сведения о directive_file см. в [формате CAB-файла Microsoft](https://go.microsoft.com/fwlink/?LinkId=226852) на сайте MSDN.

## <a name="additional-references"></a>Дополнительные материалы
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

