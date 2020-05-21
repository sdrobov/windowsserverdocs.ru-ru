---
title: endlocal
description: Справочный раздел по команде endlocal, который завершает локализацию изменений среды в пакетном файле и восстанавливает значения переменных среды перед выполнением соответствующей команды setlocal.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 765fae3c-0c0a-4639-99a4-cf613489b949
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 229914ddbfa7361738cad79903630be9e749c795
ms.sourcegitcommit: bf887504703337f8ad685d778124f65fe8c3dc13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2020
ms.locfileid: "83436889"
---
# <a name="endlocal"></a>endlocal

Завершает локализацию изменений среды в пакетном файле и восстанавливает значения переменных среды перед выполнением соответствующей команды **setlocal** .

## <a name="syntax"></a>Синтаксис

```
endlocal
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| /? | Отображение справки в командной строке. |

#### <a name="remarks"></a>Комментарии

- Команда **endlocal** не действует вне сценария или пакетного файла.

- В конце пакетного файла имеется неявная команда **endlocal** .

- Если расширения команд включены (по умолчанию включены расширения команд), команда **endlocal** восстанавливает состояние расширений команд (то есть включено или отключено) до выполнения команды **setlocal** .

> [!NOTE]
> Дополнительные сведения о включении и отключении расширений команд см. в описании [команды cmd](cmd.md).

### <a name="examples"></a>Примеры

Можно локализовать переменные среды в пакетном файле. Например, следующая программа запускает пакетную программу *суперапп* в сети, направляет выходные данные в файл и отображает его в блокноте:

```
@echo off
setlocal
path=g:\programs\superapp;%path%
call superapp>c:\superapp.out
endlocal
start notepad c:\superapp.out
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
