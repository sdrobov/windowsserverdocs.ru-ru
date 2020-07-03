---
title: Импорт программы DiskPart
description: Справочная статья по команде Import, которая импортирует группу внешних дисков в группу дисков локального компьютера.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4b9d2751-7637-4738-83b0-8c578eb28f27
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 072c012e5e2cc8d49811fbfa1cff5140b2c745a1
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85924421"
---
# <a name="import-diskpart"></a>import (diskpart)

Импортирует группу внешних дисков в группу дисков локального компьютера. Эта команда импортирует каждый диск, наявляющийся в той же группе, что и диск с фокусом.

> СУЩЕСТВЕННО Прежде чем использовать эту команду, необходимо использовать [команду Выбор диска](select-disk.md) , чтобы выбрать динамический диск в группе внешних дисков и переместить фокус на него.

## <a name="syntax"></a>Синтаксис

```
import [noerr]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| Noerr | Только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки. |

### <a name="examples"></a>Примеры

Чтобы импортировать каждый диск, расположенный в той же группе дисков, что и диск, на котором находится фокус в группе дисков локального компьютера, введите:

```
import
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда DiskPart](diskpart.md)
