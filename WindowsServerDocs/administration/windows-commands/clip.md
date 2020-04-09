---
title: клип
description: Раздел команд Windows для Clip, который перенаправляет выходные данные команды из командной строки в буфер обмена Windows.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 85322d85-3376-4806-845b-93ac77fe27bf
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0d997154a382cf39aa2b877d7a2b84f4ff34157d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80847647"
---
# <a name="clip"></a>клип

Перенаправляет выходные данные команды из командной строки в буфер обмена Windows. Затем этот текстовый вывод можно вставить в другие программы.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
<Command> | clip
clip < <FileName>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Команда \<>|Указывает команду, выходные данные которой нужно отправить в буфер обмена Windows.|
|\<имя файла >|Указывает файл, содержимое которого необходимо отправить в буфер обмена Windows.|
|/?|Отображает справку в командной строке.|

## <a name="remarks"></a>Примечания

Можно использовать команду **Clip** для копирования данных непосредственно в любое приложение, которое может получить текст из буфера обмена.

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы скопировать текущий список каталогов в буфер обмена Windows, введите:
```
dir | clip
```
Чтобы скопировать выходные данные программы с именем Generic. awk в буфер обмена Windows, введите:
```
awk -f generic.awk input.txt | clip
```
Чтобы скопировать содержимое файла с именем readme. txt в буфер обмена Windows, введите:
```
clip < readme.txt
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)