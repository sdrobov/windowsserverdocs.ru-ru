---
title: set_2
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: acf24663-1a50-4321-b48d-1717655e9476
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e91bee5f0d351e461d16ccd22478d67f26887728
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71370915"
---
# <a name="set_2"></a>set_2



Задает контекст, параметры, подробный режим и файл метаданных для создания теневой копии. Если используется без параметров, **установите** список всех текущих параметров.

## <a name="syntax"></a>Синтаксис

```
set
set context {clientaccessible | persistent [nowriters] | volatile [nowriters]}
set option {[differential | plex] [transportable] [[rollbackrecover] [txfrecover] | [noautorecover]]}
set verbose {on|off}
set metadata <MetaData.cab>
```

## <a name="set-sub-commands"></a>Задание подкоманд

|Подкоманда|Описание|
|-----------|-----------|
|Локального|Задает контекст для создания теневой копии. Синтаксис и параметры см. в разделе [Set context](set-context.md) .|
|варианты|Задает параметры для создания теневой копии. См. раздел [Set Option](set-option.md) для синтаксиса и параметров.|
|подробный|Включает или выключает режим подробных выходных данных. Синтаксис и параметры см. в разделе [Set verbose](set-verbose.md) .|
|метаданные|Задает имя и расположение файла метаданных для создания теневой копии. См. раздел [Задание метаданных](set-metadata.md) для синтаксиса и параметров.|
|/?|Отображение справки в командной строке.|

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)