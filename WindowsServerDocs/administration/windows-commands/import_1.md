---
title: импорт
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4b9d2751-7637-4738-83b0-8c578eb28f27
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ca0a15e73e4aa913ece34e083a8070be3b4b190d
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71375406"
---
# <a name="import"></a>импорт



Импортирует группу внешних дисков в группу дисков локального компьютера.

## <a name="syntax"></a>Синтаксис

```
import [noerr]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Noerr|только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки.|

## <a name="remarks"></a>Примечания

-   Команда import импортирует каждый диск, наявляющийся в той же группе, что и диск с фокусом.
-   Для выполнения этой операции необходимо выбрать динамический диск в группе внешних дисков. Используйте команду **Выбор диска** , чтобы выбрать диск и переместить фокус на него.

## <a name="BKMK_examples"></a>Примеров

Чтобы импортировать каждый диск, расположенный в той же группе дисков, что и диск, на котором находится фокус в группе дисков локального компьютера, введите:
```
import
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

