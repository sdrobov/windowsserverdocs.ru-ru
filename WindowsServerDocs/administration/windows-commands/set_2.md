---
title: set_2
description: Раздел команд Windows для set_2, который задает контекст, параметры, режим подробного протоколирования и файл метаданных для создания теневой копии.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: acf24663-1a50-4321-b48d-1717655e9476
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fa467625997824a11b2303572a063d591f59bdd6
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80834387"
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
|context|Задает контекст для создания теневой копии. Синтаксис и параметры см. в разделе [Set context](set-context.md) .|
|параметр|Задает параметры для создания теневой копии. См. раздел [Set Option](set-option.md) для синтаксиса и параметров.|
|подробный|Включает или выключает режим подробных выходных данных. Синтаксис и параметры см. в разделе [Set verbose](set-verbose.md) .|
|метаданные|Задает имя и расположение файла метаданных для создания теневой копии. См. раздел [Задание метаданных](set-metadata.md) для синтаксиса и параметров.|
|/?|Отображает справку в командной строке.|

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)