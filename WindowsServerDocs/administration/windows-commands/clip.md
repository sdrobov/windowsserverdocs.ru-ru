---
title: clip
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: b10876e115c1f0dcac3448948003852449012087
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59862395"
---
# <a name="clip"></a>clip



Перенаправляет выходные данные команды из командной строки в буфер обмена Windows. Затем можно вставить этот текстовый вывод в другие программы.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
<Command> | clip
clip < <FileName>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Команда >|Задает команду, выходные данные которого будут отправляться в буфер обмена Windows.|
|\<Имя файла >|Указывает файл, содержимое которого вы хотите отправить в буфер обмена Windows.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

Можно использовать **клипов** команду, чтобы скопировать данные непосредственно в любое приложение, которое может принимать текстовые данные из буфера обмена.

## <a name="BKMK_examples"></a>Примеры

Чтобы скопировать текущего каталога в буфер обмена Windows, введите следующую команду:
```
dir | clip
```
Чтобы скопировать выходные данные программу под названием Generic.awk в буфер обмена Windows, введите следующую команду:
```
awk -f generic.awk input.txt | clip
```
Чтобы скопировать содержимое в файл с именем файла Readme.txt в буфер обмена Windows, введите следующую команду:
```
clip < readme.txt
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)