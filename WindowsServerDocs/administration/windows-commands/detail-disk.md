---
title: диск сведений
description: Раздел команд Windows для подробного диска, в котором отображаются свойства выбранного диска и тома на этом диске.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6b09cf40-8d93-452b-b449-5242e62a4102
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0d0768d45c0f56ba549ff54064c4e74ae3048e41
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80846457"
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

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы просмотреть свойства выбранного диска и сведения о томах на диске, введите:
```
detail disk
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

