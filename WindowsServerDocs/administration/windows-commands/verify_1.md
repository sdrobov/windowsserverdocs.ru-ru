---
title: проверить
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dfe8bc91-d948-4e47-84ad-a79a60506ffa
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 840fd3609ed3aded1c9cfebd4e395ddcc6d5588b
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71363103"
---
# <a name="verify"></a>проверить



Указывает **cmd** , следует ли проверять правильность записанных файлов на диск. При использовании без параметров **Убедитесь** , что отображается текущее значение.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
verify [on | off]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[вкл \| Выкл.]|Переключает параметр **проверки** на значение ON или OFF.|
|/?|Отображение справки в командной строке.|

## <a name="BKMK_examples"></a>Примеров

Чтобы отобразить текущую настройку **проверки** , введите:
```
verify
```
Чтобы включить параметр **проверить** , введите:
```
Verify on
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)