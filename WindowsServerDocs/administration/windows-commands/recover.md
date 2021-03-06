---
title: recover
description: Справочная статья по команде Recover, которая восстанавливает читаемые данные с поврежденного или дефектного диска.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: cf9be2e3-90c8-4773-a201-dc503b91948e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ab7f502b046bf30a40b1fdd386c7faddc5c8f15a
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85931937"
---
# <a name="recover"></a>recover

Восстанавливает данные, доступные для чтения, с поврежденного или дефектного диска. Эта команда считывает файл, сектор на сектор и восстанавливает данные из хороших секторов. Данные в поврежденных секторах теряются. Так как все данные в поврежденных секторах теряются при восстановлении файла, следует восстановить только один файл за раз.

Неверные секторы, сообщаемые командой **chkdsk** , были помечены как ошибочные при подготовке диска к работе. Они не представляют опасности, и **Восстановление** не влияет на них.

## <a name="syntax"></a>Синтаксис

```
recover [<drive>:][<path>]<filename>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
|--|--|
| `[<drive>:][<path>]<filename>` | Указывает имя файла (и расположение файла, если он не находится в текущем каталоге), который требуется восстановить. Требуется *имя файла* , а подстановочные знаки не поддерживаются. |
| /? | Отображение справки в командной строке. |

### <a name="examples"></a>Примеры

Чтобы восстановить файл *story.txt* в каталоге *\Фиктион* на диске D, введите:

```
recover d:\fiction\story.txt
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
