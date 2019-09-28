---
title: break
description: 'Раздел команд Windows для **break_1** : задает или очищает расширенную проверку CTRL + C в системах MS-DOS. Если используется без параметров, параметр **break** отображает текущее значение. '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c89b7357-d69e-4141-826e-73c9ba0fc630
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 73afdac29efbfd9efec88d297cf4185ca1b92d62
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380488"
---
# <a name="break"></a>break



Задает или очищает расширенную проверку CTRL + C в системах MS-DOS. Если используется без параметров, параметр **break** отображает текущее значение.

> [!NOTE]
> Эта команда больше не используется. Она включена только для обеспечения совместимости с существующими файлами MS-DOS и ее применение не влияет на результат, поскольку необходимые действия выполняются автоматически.

## <a name="syntax"></a>Синтаксис

```
break=[on|off]
```

## <a name="remarks"></a>Примечания

Если расширения команд включены и работают на платформе Windows, при вставке команды **break** в пакетный файл при отладке отладчика он переходит в жестко запрограммированную точку останова.

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)