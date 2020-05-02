---
title: nslookup set class
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ed826400-40da-42b6-b7f0-95db73790723
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b1ae3a5336815a5273aafa976b1dcad8b60fac9b
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723653"
---
# <a name="nslookup-set-class"></a>nslookup set class



Изменяет класс запроса. Класс указывает группу протоколов сведений.

## <a name="syntax"></a>Синтаксис

```
set class=<Class>
```

### <a name="parameters"></a>Параметры

| Параметр |                                                                                                                                    Описание                                                                                                                                    |
|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| \<Class>  | Класс по умолчанию находится в. Ниже перечислены допустимые значения для этой команды.</br>-IN: указывает класс Интернета.</br>-CHAOS: указывает класс Chaos.</br>-ХЕСИОД: указывает класс MIT Афина Хесиод.</br>-ANY: указывает любой из перечисленных выше подстановочных знаков. |
|   {Справка   |                                                                                                                                        ?}                                                                                                                                         |

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)