---
title: Имитация восстановления
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d883d94c-3cb1-4848-9d74-1b4378044b31
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 09b626939c13d4e38a983435b45d8c47ee2b93a4
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59817255"
---
# <a name="simulate-restore"></a>Имитация восстановления



Проверяет модуль записи участие в сеансах восстановления на компьютере без выдачи **PreRestore** или **PostRestore** события для записи.

## <a name="syntax"></a>Синтаксис

```
simulate restore
```

## <a name="remarks"></a>Примечания

-   **Имитация восстановления** используется для проверки независимо от того, имеется ли восстановление с помощью модулей записи может быть успешной.
-   Перед использованием **имитации восстановления**, необходимо загрузить файл метаданных DiskShadow с помощью **загрузить метаданные** команды. Это загружает выбранные записи и компоненты для восстановления.

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)