---
title: endlocal
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 765fae3c-0c0a-4639-99a4-cf613489b949
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4958c5419ed4f6374f7c6ecf09bdf67f61134d93
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80845117"
---
# <a name="endlocal"></a>endlocal



Завершает локализацию изменений среды в пакетном файле и восстанавливает значения переменных среды перед выполнением соответствующей команды **setlocal** .

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
endlocal
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/?|Отображает справку в командной строке.|

## <a name="remarks"></a>Примечания

-   Команда **endlocal** не действует вне сценария или пакетного файла.
-   В конце пакетного файла имеется неявная команда **endlocal** .
-   Если расширения команд включены (по умолчанию включены расширения команд), команда **endlocal** восстанавливает состояние расширений команд (то есть включено или отключено) до выполнения команды **setlocal** .

> [!NOTE]
> Дополнительные сведения о включении и отключении расширений команд см. в разделе [cmd](cmd.md).

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Можно локализовать переменные среды в пакетном файле. Например, следующая программа запускает пакетную программу суперапп в сети, направляет выходные данные в файл и отображает его в блокноте:
```
@echo off
setlocal
path=g:\programs\superapp;%path%
call superapp>c:\superapp.out
endlocal
start notepad c:\superapp.out
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)