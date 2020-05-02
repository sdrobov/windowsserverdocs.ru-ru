---
title: set_2
description: Справочный раздел по set_2, который задает контекст, параметры, режим подробного протоколирования и файл метаданных для создания теневой копии.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: acf24663-1a50-4321-b48d-1717655e9476
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 655f379dd8c2d633aad0cbb470b17c6ccb90c4f7
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721873"
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
|контекст|Задает контекст для создания теневой копии. Синтаксис и параметры см. в разделе [Set context](set-context.md) .|
|Параметр|Задает параметры для создания теневой копии. См. раздел [Set Option](set-option.md) для синтаксиса и параметров.|
|verbose|Включает или выключает режим подробных выходных данных. Синтаксис и параметры см. в разделе [Set verbose](set-verbose.md) .|
|метаданные|Задает имя и расположение файла метаданных для создания теневой копии. См. раздел [Задание метаданных](set-metadata.md) для синтаксиса и параметров.|
|/?|Отображение справки в командной строке.|

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)