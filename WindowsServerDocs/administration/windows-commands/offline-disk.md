---
title: автономный диск
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8fb9b3c3-0b2c-4192-a2e7-f706292653e3
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f28d473cdb557d6adb3aaf235bebdfbc4e78b24a
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71372598"
---
# <a name="offline-disk"></a>автономный диск



Переводит сетевой диск в состояние "вне сети".

> [!IMPORTANT]
> Эта команда DiskPart недоступна ни в одном из выпусков Windows Vista.

## <a name="syntax"></a>Синтаксис

```
offline disk [noerr]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Noerr|только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки.|

## <a name="remarks"></a>Примечания

-   Эта команда работает с дисками в режиме сети SAN. Он изменяет режим SAN на "вне сети".
-   Если динамический диск в группе дисков переведен в режим «вне сети», то состояние диска изменится на « **отсутствует** », а в группе отобразится неподключенный диск. Отсутствующий диск перемещается в недопустимую группу. Если динамический диск является последним в группе, то состояние диска изменится на **автономный**, а пустая группа будет удалена.
-   Для завершения команды " **автономный диск** " необходимо выбрать диск. Используйте команду **Выбор диска** , чтобы выбрать диск и переместить фокус на него.

## <a name="BKMK_examples"></a>Примеров

Чтобы перевести диск с фокусом в режим вне сети, введите:
```
offline disk
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

