---
title: проверка
description: Раздел команд Windows для проверки, который указывает **cmd** , следует ли проверять правильность записанных файлов на диск.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: dfe8bc91-d948-4e47-84ad-a79a60506ffa
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 91a0777999a604a23e2de83eda6b89c926cb241c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80830057"
---
# <a name="verify"></a>проверка



Указывает **cmd** , следует ли проверять правильность записанных файлов на диск. При использовании без параметров **Убедитесь** , что отображается текущее значение.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
verify [on | off]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[вкл \| Off]|Переключает параметр **проверки** на значение ON или OFF.|
|/?|Отображает справку в командной строке.|

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы отобразить текущую настройку **проверки** , введите:
```
verify
```
Чтобы включить параметр **проверить** , введите:
```
Verify on
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)