---
title: nslookup set class
description: Справочный раздел для команды nslookup set Class, которая изменяет класс запроса.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ed826400-40da-42b6-b7f0-95db73790723
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e939be13eedcab557dc6dcbe16f2e83f810c20d5
ms.sourcegitcommit: 99d548141428c964facf666c10b6709d80fbb215
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2020
ms.locfileid: "84721567"
---
# <a name="nslookup-set-class"></a>nslookup set class

Изменяет класс запроса. Класс указывает группу протоколов сведений.

## <a name="syntax"></a>Синтаксис

```
set class=<class>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<class>` | Допустимые значения:<ul><li>**В:** Указывает класс Интернета. Это значение по умолчанию.</li><li>**Chaos:** Указывает класс Chaos.</li><li>**Хесиод:** Указывает класс MIT Афина Хесиод.</li><li>**Все:** Задает использование любого из приведенных выше значений.</li></ul> |
| /? | Отображение справки в командной строке. |
| /help | Отображение справки в командной строке. |

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
