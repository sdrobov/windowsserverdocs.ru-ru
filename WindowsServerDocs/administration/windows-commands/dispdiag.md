---
title: dispdiag
description: Раздел команд Windows для диспдиаг, в котором в журналах отображаются сведения о файле.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5079e1dd-b57c-44ed-970f-e6b409369e03
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 498294aa6678cc4904880128bca55d7900c91db5
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80845387"
---
# <a name="dispdiag"></a>dispdiag

Журналы отображают сведения в файле.

## <a name="syntax"></a>Синтаксис

```
dispdiag [-testacpi] [-d] [-delay <Seconds>] [-out <FilePath>]
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|-тестакпи|Выполняет тестовую диагностику с сочетанием клавиш. Отображает имя ключа, код и код сканирования для любой клавиши, нажатой во время теста.|
|-d|Создает файл дампа с результатами теста.|
|— задержка \<секунды >|Задерживает сбор данных в указанное время в *секундах*.|
|-out \<FilePath >|Указывает путь и имя файла для сохранения собранных данных. Это должен быть последний параметр.|
|-?|Отображает доступные параметры команды и предоставляет справку по их использованию.|