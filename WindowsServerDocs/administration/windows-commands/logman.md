---
title: logman
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 574a5203-5b3b-4759-a678-f26d00dde447
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bb6654cce0e23ac08a2fa6334d6144b08c8b65f3
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80840407"
---
# <a name="logman"></a>logman

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

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
