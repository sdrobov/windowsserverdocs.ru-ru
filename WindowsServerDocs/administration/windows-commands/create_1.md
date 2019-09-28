---
title: create
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 837aa449-9b60-41ae-9ef1-ef67af6e5918
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2245efb6c3bce8aecf8edf730694804ffbdc3d80
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71378774"
---
# <a name="create"></a>create



запускает процесс создания теневой копии с использованием текущего контекста и настроек параметров. Требуется по крайней мере один том в наборе теневых копий.

## <a name="syntax"></a>Синтаксис

```
create
```

## <a name="remarks"></a>Примечания

-   Перед использованием команды " **создать** " необходимо добавить по крайней мере один том с помощью команды " **Добавить том** ".
-   Чтобы указать полную резервную копию, а не резервную копию, можно использовать команду **начать резервное** копирование.
-   После выполнения команды **CREATE** можно использовать команду **exec** , чтобы выполнить повторяющийся скрипт для резервного копирования из теневой копии.

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)