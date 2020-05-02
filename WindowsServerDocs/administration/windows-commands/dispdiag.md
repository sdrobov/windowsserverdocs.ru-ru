---
title: dispdiag
description: Справочный раздел по диспдиаг, в котором в журнале отображаются сведения о файле.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5079e1dd-b57c-44ed-970f-e6b409369e03
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f9f44e261b9c46157fb3e6bb7f9105af2480a60b
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719407"
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
|-задержка \<секунд>|Задерживает сбор данных в указанное время в *секундах*.|
|- \<FilePath>|Указывает путь и имя файла для сохранения собранных данных. Это должен быть последний параметр.|
|-?|Отображает доступные параметры команды и предоставляет справку по их использованию.|