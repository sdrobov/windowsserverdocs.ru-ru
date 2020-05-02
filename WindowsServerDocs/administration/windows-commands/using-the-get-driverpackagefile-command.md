---
title: Get-Дриверпаккажефиле
description: Справочный раздел по Get-Дриверпаккажефиле, в котором отображаются сведения о пакете драйверов, включая драйверы и файлы, которые он содержит.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f01a2c67-7e9c-4aad-b625-383f5a1fca25
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 71fc38e31471a1deb9d6be29b04d3cd911be1bd6
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719934"
---
# <a name="get-driverpackagefile"></a>Get-Дриверпаккажефиле

Отображает сведения о пакете драйверов, включая драйверы и файлы, которые он содержит.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /Get-DriverPackageFile /InfFile:<Inf File path> [/Architecture:{x86 | ia64 | x64}] [/Show:{Drivers | Files | All}]
```

### <a name="parameters"></a>Параметры

|         Параметр         |                              Описание                               |
|---------------------------|------------------------------------------------------------------------|
| /Инффиле:\<путь к INF-файлу> | Указывает полный путь и имя файла INF-файла пакета драйвера. |
|    [/Арчитектуре: {x86    |                                  ia64                                  |
|     [/Show: {Drivers      |                                 Файлы                                  |

## <a name="examples"></a>Примеры

Чтобы просмотреть сведения о файле драйвера, введите:
```
WDSUTIL /Get-DriverPackageFile /InfFile:C:\temp\1394.inf /Architecture:x86
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)