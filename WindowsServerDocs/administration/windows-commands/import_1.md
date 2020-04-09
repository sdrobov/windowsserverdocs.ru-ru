---
title: импорт
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4b9d2751-7637-4738-83b0-8c578eb28f27
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7e098e7133bca18e1a6ba683e525783af17c3958
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80842137"
---
# <a name="import"></a>импорт



Импортирует группу внешних дисков в группу дисков локального компьютера.

## <a name="syntax"></a>Синтаксис

```
import [noerr]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Noerr|Только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки.|

## <a name="remarks"></a>Примечания

-   Команда import импортирует каждый диск, наявляющийся в той же группе, что и диск с фокусом.
-   Для выполнения этой операции необходимо выбрать динамический диск в группе внешних дисков. Используйте команду **Выбор диска** , чтобы выбрать диск и переместить фокус на него.

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы импортировать каждый диск, расположенный в той же группе дисков, что и диск, на котором находится фокус в группе дисков локального компьютера, введите:
```
import
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

