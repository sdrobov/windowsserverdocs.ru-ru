---
title: Сведения о томе
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 38f2bc75-2ed6-4e80-aa74-ab83133db1cd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b7cae6dc9b82992b58c4f94801f90c0b7072492b
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59856925"
---
# <a name="detail-volume"></a>Сведения о томе



Отображает диски, на которых размещен текущий том.

## <a name="syntax"></a>Синтаксис

```
detail volume
```

## <a name="remarks"></a>Примечания

-   Для успешного выполнения этой операции необходимо выбрать том. Используйте **выберите том** команду, чтобы выбрать том и перетянуть внимание к нему.
-   Сведения о томе не применяются к томам, только для чтения, например дисковод компакт-дисков или DVD-диска.

## <a name="BKMK_examples"></a>Примеры

Чтобы просмотреть все диски, в которых находится текущего тома, введите следующую команду:
```
detail volume
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)

