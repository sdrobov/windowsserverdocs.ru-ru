---
title: exit
description: Справочная статья для выхода, которая выходит из интерпретатора команд.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d3cee4a2-6210-46f0-b8e4-7381c3c4e530
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d28f15ba1453b32d8e464fd768a3b7895819d11c
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85931456"
---
# <a name="exit"></a>exit

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Выход из интерпретатора команд или текущего пакетного скрипта.

## <a name="syntax"></a>Синтаксис

```
exit [/b] [<exitcode>]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| /b | Выход из текущего пакетного скрипта вместо выхода из Cmd.exe. Если выполняется из-за пределов пакетного скрипта, выполняет выход из Cmd.exe. |
| `<exitcode>` | Указывает числовое число. Если указан параметр **/b** , переменной среды ERRORLEVEL присваивается это число. Если интерпретатор команд закрывается, код завершения процесса устанавливается в это число. |
| /? | Отображение справки в командной строке. |

## <a name="examples"></a>Примеры

Чтобы закрыть интерпретатор команд, введите:

```
exit
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
