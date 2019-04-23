---
title: append
description: 'Раздел Windows команды для '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9c3fea20-9502-40ad-a442-7a927aad88eb
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: abf7713b3fd5bbb6172969ca1cc39cbbbbafafc6
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59881985"
---
# <a name="append"></a>append



Позволяет программам открывать файлы данных в указанных каталогах, как если бы они были в текущем каталоге. При использовании без параметров, **append** отображает список добавленных каталогов.

> [!NOTE]
> Эта команда не поддерживается в Windows 10.
>

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
append [[<Drive>:]<Path>[;...]] [/x[:on|:off]] [/path:[:on|:off] [/e] 
append ;
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[\<Диска >:]<Path>|Указывает, диск и каталог для добавления.|
|/x:on|Применяет присоединенных каталогов для поиска файлов и запуск программ.|
|/x:off|Присоединенных каталогов применяется только к запросам для открытия файлов.</br>**/ x: off** значение по умолчанию.|
|/ PATH: на|Применяет присоединенных каталогов для запросов файлов, которые уже укажите путь. **/ PATH: на** значение по умолчанию.|
|/ PATH: off|Отключает последствия **/path: на**.|
|/e|Сохраняет копию списка добавленных каталогов в переменную среды с именем APPEND. **/e** может использоваться только при первом использовании **append** после запуска системы.|
|;|Очищает список добавленных каталогов.|
|/?|Отображение справки в командной строке.|

## <a name="BKMK_examples"></a>Примеры

Чтобы очистить список присоединенных каталогов, введите следующую команду:
```
append ;
```
Чтобы сохранить копию присоединенных каталог в переменную среды с именем APPEND, введите:
```
append /e
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)
