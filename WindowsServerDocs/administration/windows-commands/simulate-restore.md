---
title: Имитировать восстановление
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: d6652fea4e74c706fcc03b8a547fab771a7c0191
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71370880"
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

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)