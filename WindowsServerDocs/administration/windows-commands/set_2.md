---
title: set_2
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 3f5523646fddbfec31cb3900fc09230efc1c7813
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59862615"
---
# <a name="set2"></a>set_2



Задает контекст, параметры, режим подробного протоколирования и файл метаданных для теневой копии. При использовании без параметров, **задать** отображает список всех текущих параметров.

## <a name="syntax"></a>Синтаксис

```
set
set context {clientaccessible | persistent [nowriters] | volatile [nowriters]}
set option {[differential | plex] [transportable] [[rollbackrecover] [txfrecover] | [noautorecover]]}
set verbose {on|off}
set metadata <MetaData.cab>
```

## <a name="set-sub-commands"></a>Вложенные команды set

|Подкоманда|Описание|
|-----------|-----------|
|Контекст|Задает контекст для теневой копии. См. в разделе [контекст набора](set-context.md) для синтаксиса и параметров.|
|варианты|Задает параметры для теневой копии. См. в разделе [задания параметра](set-option.md) для синтаксиса и параметров.|
|подробный|Включает режим подробного вывода или выключает. См. в разделе [задать подробный журнал](set-verbose.md) для синтаксиса и параметров.|
|метаданные|Задает имя и расположение файла метаданных создания тени. См. в разделе [задать метаданные](set-metadata.md) для синтаксиса и параметров.|
|/?|Отображение справки в командной строке.|

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)