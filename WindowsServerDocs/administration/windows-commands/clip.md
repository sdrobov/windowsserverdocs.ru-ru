---
title: clip
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 85322d85-3376-4806-845b-93ac77fe27bf
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 82186869782c47f41930d46b4c33a710e6addedf
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71379351"
---
# <a name="clip"></a>clip



Перенаправляет выходные данные команды из командной строки в буфер обмена Windows. Затем этот текстовый вывод можно вставить в другие программы.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
<Command> | clip
clip < <FileName>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Команда \<>|Указывает команду, выходные данные которой нужно отправить в буфер обмена Windows.|
|\<имя файла >|Указывает файл, содержимое которого необходимо отправить в буфер обмена Windows.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Замечания

Можно использовать команду **Clip** для копирования данных непосредственно в любое приложение, которое может получить текст из буфера обмена.

## <a name="BKMK_examples"></a>Примеров

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

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)