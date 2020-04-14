---
title: Get-Дриверпаккажефиле
description: Раздел команд Windows для Get-Дриверпаккажефиле, в котором отображаются сведения о пакете драйверов, включая драйверы и файлы, которые он содержит.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f01a2c67-7e9c-4aad-b625-383f5a1fca25
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d485a24479aa857270968a1bff7bd55a014347a3
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80831037"
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
| /Инффиле:\<путь к файлу INF > | Указывает полный путь и имя файла INF-файла пакета драйвера. |
|    [/Арчитектуре: {x86    |                                  ia64                                  |
|     [/Show: {Drivers      |                                 Файлы                                  |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы просмотреть сведения о файле драйвера, введите:
```
WDSUTIL /Get-DriverPackageFile /InfFile:C:\temp\1394.inf /Architecture:x86
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)