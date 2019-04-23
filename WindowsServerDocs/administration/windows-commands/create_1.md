---
title: создание
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 70a8f53d9cb90fc36a76b11de2f93da71874617a
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59881275"
---
# <a name="create"></a>создание



Запускает процесс создания теневой копии, с использованием текущих параметров контекста и параметр. Требуется по крайней мере один том в наборе теневого копирования.

## <a name="syntax"></a>Синтаксис

```
create
```

## <a name="remarks"></a>Примечания

-   Необходимо добавить по крайней мере один том с **добавить том** команды перед использованием **создать** команды.
-   Можно использовать **запуска архивации** команду, чтобы указать полную резервную копию, а не резервной копии.
-   После того, как **создать** команды можно использовать **exec** команду, чтобы запустить сценарий дублирования для резервного копирования из теневой копии.

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)