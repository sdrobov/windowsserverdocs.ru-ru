---
title: dispdiag
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5079e1dd-b57c-44ed-970f-e6b409369e03
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9c96c70aac1b3329e050fa8b02743e61fed44d15
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59831465"
---
# <a name="dispdiag"></a>dispdiag



В журналах отображаются сведения в файл.

## <a name="syntax"></a>Синтаксис

```
dispdiag [-testacpi] [-d] [-delay <Seconds>] [-out <FilePath>]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|-testacpi|Запускает тест диагностики сочетание клавиш. Отображает имя ключа, кода и проверки кода для любого ключа нажаты во время теста.|
|-d|Создает файл дампа с результатами теста.|
|-delay \<секунд >|Задерживает сбор данных на указанное время в *секунд*.|
|-out \<FilePath >|Указывает путь и имя файла для сохранения собранных данных. Это должен быть последним параметром.|
|-?|Отображает доступные параметры и предоставляет справку по их использованию.|