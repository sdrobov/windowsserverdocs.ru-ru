---
title: проверка
description: Справочный раздел для проверки **, указывающий, следует ли убедиться** , что файлы правильно записаны на диск.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: dfe8bc91-d948-4e47-84ad-a79a60506ffa
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f7fc35b37d5e0a429e1ecc2ebefc117804a0c645
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720292"
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
|[вкл \| . откл.]|Переключает параметр **проверки** на значение ON или OFF.|
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