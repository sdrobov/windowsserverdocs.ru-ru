---
title: simulate restore
description: Справочная статья по моделированию Restore, которая проверяет участие модуля записи в сеансах восстановления на компьютере без выдачи событий предварительного восстановления или восстановления в модули записи.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d883d94c-3cb1-4848-9d74-1b4378044b31
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7cc247848ef4fac1e3a6537247f640f3533c2bcd
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85936351"
---
# <a name="simulate-restore"></a>Имитировать восстановление

Выполняет тесты, вовлеченные в сеансы восстановления на компьютере без выдачи событий предварительного **восстановления** или **восстановления** в модули записи.

## <a name="syntax"></a>Синтаксис

```
simulate restore
```

## <a name="remarks"></a>Примечания

-   **Имитация восстановления** используется для проверки успешности восстановления с помощью модулей записи.
-   Прежде чем можно будет использовать **имитацию восстановления**, необходимо загрузить файл метаданных Diskshadow с помощью команды **загрузить метаданные** . При этом загружаются выбранные модули записи и компоненты для восстановления.

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)