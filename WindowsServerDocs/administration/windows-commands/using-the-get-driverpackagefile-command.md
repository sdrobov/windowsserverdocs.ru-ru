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
ms.openlocfilehash: ed9518fae07745502d01dc0084b7443a1332db83
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59859805"
---
# <a name="using-the-get-driverpackagefile-command"></a>С помощью команды get-DriverPackageFile



Отображает сведения о пакете драйверов, включая драйверы и файлы, содержащиеся в ней.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /Get-DriverPackageFile /InfFile:<Inf File path> [/Architecture:{x86 | ia64 | x64}] [/Show:{Drivers | Files | All}]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/ INF-файл:\<путь к INF-файла >|Указывает полный путь и имя пакета драйвера INF-файла.|
|[/ Архитектура: {x86 | IA64 | x64}]|Задает архитектуру пакета драйвера.|
|[/ Show: {драйверы | Файлы | Все}]|Указывает сведения о пакете для отображения. Если **/Показать** не указан, по умолчанию используется для возвращения только драйвер метаданных пакета. **Драйверы** отображается список драйверов в пакете. **Файлы** отображает список файлов в пакете. **Все** отображает файлы и драйверы.|

## <a name="BKMK_examples"></a>Примеры

Чтобы просмотреть сведения о файле драйвера, введите следующую команду:
```
WDSUTIL /Get-DriverPackageFile /InfFile:"C:\temp\1394.inf" /Architecture:x86
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)