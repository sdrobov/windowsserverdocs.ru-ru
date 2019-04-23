---
title: endlocal
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 765fae3c-0c0a-4639-99a4-cf613489b949
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3e516b2bf9e8a45ada910dfbd93e3ed5e7d86c14
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59862145"
---
# <a name="endlocal"></a>endlocal



Завершает локальных изменений среды в пакетном файле и восстанавливает переменные среды для их значения до соответствующего **setlocal** была выполнена команда.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
endlocal
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

-   **Endlocal** команда не оказывает влияния вне сценария или пакетного файла.
-   Имеется неявный **endlocal** команду в конце пакетного файла.
-   Если включены расширения команд (команда расширения включены по умолчанию), **endlocal** команда восстанавливает состояние расширения команд (то есть, включена или отключена), существовавшие до соответствующего  **SETLOCAL** была выполнена команда.

> [!NOTE]
> Дополнительные сведения о включении и отключении расширения команд см. в разделе [Cmd](cmd.md).

## <a name="BKMK_examples"></a>Примеры

Вы можете локализовать переменные среды в пакетном файле. Например следующая программа запускает пакетная программа superapp в сети, направляет вывод в файл и открывает файл в блокноте:
```
@echo off
setlocal
path=g:\programs\superapp;%path%
call superapp>c:\superapp.out
endlocal
start notepad c:\superapp.out
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)