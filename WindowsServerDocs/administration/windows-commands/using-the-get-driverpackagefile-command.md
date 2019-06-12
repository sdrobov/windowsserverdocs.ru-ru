---
title: С помощью команды get-DriverPackageFile
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f01a2c67-7e9c-4aad-b625-383f5a1fca25
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 264bdb6d51622e6323be00b44014b86cd9662e61
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66440501"
---
# <a name="using-the-get-driverpackagefile-command"></a>С помощью команды get-DriverPackageFile



Отображает сведения о пакете драйверов, включая драйверы и файлы, содержащиеся в ней.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /Get-DriverPackageFile /InfFile:<Inf File path> [/Architecture:{x86 | ia64 | x64}] [/Show:{Drivers | Files | All}]
```

## <a name="parameters"></a>Параметры

|         Параметр         |                              Описание                               |
|---------------------------|------------------------------------------------------------------------|
| / INF-файл:\<путь к INF-файла > | Указывает полный путь и имя пакета драйвера INF-файла. |
|    [/ Архитектура: {x86    |                                  IA64                                  |
|     [/ Show: {драйверы      |                                 Файлы                                  |

## <a name="BKMK_examples"></a>Примеры

Чтобы просмотреть сведения о файле драйвера, введите следующую команду:
```
WDSUTIL /Get-DriverPackageFile /InfFile:"C:\temp\1394.inf" /Architecture:x86
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)