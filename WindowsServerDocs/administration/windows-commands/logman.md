---
title: logman
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 574a5203-5b3b-4759-a678-f26d00dde447
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9aed5a83c503c03f52757abf525aa5d122f41466
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724274"
---
# <a name="logman"></a>logman

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

**Logman** создает сеанс трассировки событий и журналы производительности и управляет ими, а также поддерживает многие функции системного монитора из командной строки.
## <a name="syntax"></a>Синтаксис
```
logman [create | query | start | stop | delete| update | import | export | /?] [options]
```
## <a name="actions"></a>Действия
|Действие|Описание|
|-----|--------|
|[logman create](logman-create.md)|Создание счетчика, трассировки, сборщика данных конфигурации или API.|
|[logman query](logman-query.md)|запросите свойства сборщика данных.|
|[logman start &#124; stop](logman-start-stop.md)|Запуск или завершение сбора данных.|
|[logman delete](logman-delete.md)|Удаление существующего сборщика данных.|
|[logman update](logman-update.md)|Обновление свойств существующего сборщика данных.|
|[logman import &#124; export](logman-import-export.md)|Импорт набора сборщиков данных из XML-файла или экспорт набора сборщиков данных в XML-файл.|
