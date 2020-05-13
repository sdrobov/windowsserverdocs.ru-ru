---
title: dispdiag
description: Справочный раздел по команде диспдиаг, в котором в журнале отображаются сведения о файле.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5079e1dd-b57c-44ed-970f-e6b409369e03
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ff4e3690ec3b2c9d473f05027d5637eda124d0ba
ms.sourcegitcommit: aed942d11f1a361fc1d17553a4cf190a864d1268
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/12/2020
ms.locfileid: "83235222"
---
# <a name="dispdiag"></a>dispdiag

Журналы отображают сведения в файле.

## <a name="syntax"></a>Синтаксис

```
dispdiag [-testacpi] [-d] [-delay <seconds>] [-out <filepath>]
```

#### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| -тестакпи | Выполняет тестовую диагностику с сочетанием клавиш. Отображает имя ключа, код и код сканирования для любой клавиши, нажатой во время теста. |
| -d | Создает файл дампа с результатами теста. |
| -Delay`<seconds>` | Задерживает сбор данных в указанное время в *секундах*. |
| -out`<filepath>`  | Указывает путь и имя файла для сохранения собранных данных. Это должен быть последний параметр. |
| -? | Отображает доступные параметры команды и предоставляет справку по их использованию. |

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
