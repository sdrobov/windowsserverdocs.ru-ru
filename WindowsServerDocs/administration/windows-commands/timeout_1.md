---
title: timeout
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e26b4a84-0e30-46e1-aa10-0667b7d3cb4c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 09f294eb78a8868b4e3962557a36199b69fae0c9
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71385770"
---
# <a name="timeout"></a>timeout



Приостанавливает работу обработчика команд в течение указанного числа секунд.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
timeout /t <TimeoutInSeconds> [/nobreak] 
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/t @no__t — 0TimeoutInSeconds >|Указывает десятичное число секунд (от-1 до 99999), по истечении которого обработчик команд продолжит обработку. Значение-1 заставляет компьютер бесконечно ждать нажатия клавиши.|
|/нобреак|Задает игнорирование пользовательских клавиш.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

-   Команда **timeout** обычно используется в пакетных файлах.
-   Нажатие клавиши пользователя возобновляет выполнение командного процессора немедленно, даже если истек период ожидания.
-   При использовании в сочетании с командой **Sleep** **время ожидания** аналогично команде **Pause** .

## <a name="BKMK_examples"></a>Примеров

Чтобы приостановить обработчик команд в течение десяти секунд, введите:
```
timeout /t 10
```
Чтобы приостановить обработчик команд в течение 100 секунд и проигнорировать все нажатия клавиш, введите:
```
timeout /t 100 /nobreak
```
Чтобы приостановить процессор команд в течение неограниченного времени до нажатия клавиши, введите:
```
timeout /t -1
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
