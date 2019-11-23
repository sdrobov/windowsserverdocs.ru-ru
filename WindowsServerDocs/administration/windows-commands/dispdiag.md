---
title: dispdiag
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 9b640883a207648d2ef6c9a7d6e5366cd0bb384c
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71377764"
---
# <a name="dispdiag"></a>dispdiag



Журналы отображают сведения в файле.

## <a name="syntax"></a>Синтаксис

```
dispdiag [-testacpi] [-d] [-delay <Seconds>] [-out <FilePath>]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|-тестакпи|Выполняет тестовую диагностику с сочетанием клавиш. Отображает имя ключа, код и код сканирования для любой клавиши, нажатой во время теста.|
|-d|Создает файл дампа с результатами теста.|
|— задержка \<секунды >|Задерживает сбор данных в указанное время в *секундах*.|
|-out \<FilePath >|Указывает путь и имя файла для сохранения собранных данных. Это должен быть последний параметр.|
|-?|Отображает доступные параметры команды и предоставляет справку по их использованию.|