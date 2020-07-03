---
title: nslookup set class
description: Справочная статья по команде nslookup set Class, которая изменяет класс запроса.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ed826400-40da-42b6-b7f0-95db73790723
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 073f27f6f10721b11e6d0889d1cb8c16f15db283
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85934427"
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
