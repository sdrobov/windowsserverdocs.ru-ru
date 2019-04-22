---
title: восстановить
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cf9be2e3-90c8-4773-a201-dc503b91948e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 805f63e95bcb72416cdacea4ba792af8c9a96c06
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59813105"
---
# <a name="recover"></a>восстановить



Восстанавливает читаемой информации из поврежденном диске.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
recover [<Drive>:][<Path>]<FileName>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[\<Диска >:] [<Path>]<FileName>|Указывает расположение и имя файла, который вы хотите восстановить. *Имя файла* является обязательным.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

-   **Восстановить** команда считывает файл сектор за сектором и восстанавливает данные считана. Данные в поврежденных секторов теряются.
-   Сообщаемое поврежденных секторов **chkdsk** были помечены как «плохое», при форматировании диска для операции. Они могут представлять опасность, а **восстановить** никак не влияет на их.
-   Так как все данные в поврежденных секторов теряется при восстановлении файла, следует восстанавливать только один файл за раз.
-   Нельзя использовать подстановочные знаки (**&#42;** и **?**) с **восстановить** команды. Необходимо указать файл (и расположение файла, если он не находится в текущем каталоге).

## <a name="BKMK_examples"></a>Примеры

Чтобы восстановить файл Story.txt в каталоге \Fiction на диске D, введите следующую команду:
```
recover d:\fiction\story.txt 
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)