---
title: диск сведений
description: Справочный раздел для диска Details, который отображает свойства выбранного диска и томов на этом диске.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6b09cf40-8d93-452b-b449-5242e62a4102
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a746506d6c9609e3214dbd48e5fa91f52d16ab4d
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82710516"
---
# <a name="detail-disk"></a>диск сведений

Отображает свойства выбранного диска и тома на этом диске.

## <a name="syntax"></a>Синтаксис

```
detail disk
```

## <a name="remarks"></a>Примечания

-   Для выполнения этой операции необходимо выбрать диск. Используйте команду **Выбор диска** , чтобы выбрать диск и переместить фокус на него.
-   Если выбранный диск является виртуальным жестким диском (VHD), то **подробный диск** сообщает тип шины диска как виртуальный.

## <a name="examples"></a>Примеры

Чтобы просмотреть свойства выбранного диска и сведения о томах на диске, введите:
```
detail disk
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

