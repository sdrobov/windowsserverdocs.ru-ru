---
title: подробный том
description: Раздел команд Windows для подробного тома, в котором отображаются диски, на которых находится текущий том.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 38f2bc75-2ed6-4e80-aa74-ab83133db1cd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1f0441beba769066c593e77b55b9266918e5f778
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80846328"
---
# <a name="detail-volume"></a>подробный том

Отображает диски, на которых находится текущий том.

## <a name="syntax"></a>Синтаксис

```
detail volume
```

## <a name="remarks"></a>Примечания

-   Для выполнения этой операции необходимо выбрать том. Используйте команду **выбрать том** , чтобы выбрать том и переместить фокус на него.
-   Сведения о томе неприменимы к томам только для чтения, например DVD-дискам или дисководам компакт-дисков.

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы просмотреть все диски, в которых находится текущий том, введите:
```
detail volume
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

