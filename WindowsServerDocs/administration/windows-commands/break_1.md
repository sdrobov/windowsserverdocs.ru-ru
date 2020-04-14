---
title: break
description: Раздел команд Windows для break_1, который задает или очищает расширенную проверку CTRL + C в системах MS-DOS.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c89b7357-d69e-4141-826e-73c9ba0fc630
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 809a9321b8b4f8b2d201582f767da132076826d4
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848367"
---
# <a name="break"></a>break

Задает или очищает расширенную проверку CTRL + C в системах MS-DOS. Если используется без параметров, параметр **break** отображает текущее значение.

> [!NOTE]
> Эта команда больше не используется. Она включена только для сохранения совместимости с существующими файлами MS-DOS, однако никак не влияет на результат при использовании в командной строке, поскольку соответствующие функциональные возможности являются автоматическими.

## <a name="syntax"></a>Синтаксис

```
break=[on|off]
```

## <a name="remarks"></a>Примечания

Если расширения команд включены и работают на платформе Windows, при вставке команды **break** в пакетный файл при отладке отладчика он переходит в жестко запрограммированную точку останова.

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)