---
title: проверка
description: Справочная статья для проверки, которая указывает **cmd** , следует ли проверять правильность записанных файлов на диск.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: dfe8bc91-d948-4e47-84ad-a79a60506ffa
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1455705d409e0273e85135a183279835e7238d7a
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85931310"
---
# <a name="verify"></a>проверка



Указывает **cmd** , следует ли проверять правильность записанных файлов на диск. При использовании без параметров **Убедитесь** , что отображается текущее значение.



## <a name="syntax"></a>Синтаксис

```
verify [on | off]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[вкл. \| Откл.]|Переключает параметр **проверки** на значение ON или OFF.|
|/?|Отображение справки в командной строке.|

## <a name="examples"></a>Примеры

Чтобы отобразить текущую настройку **проверки** , введите:
```
verify
```
Чтобы включить параметр **проверить** , введите:
```
Verify on
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)