---
title: nslookup set class
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ed826400-40da-42b6-b7f0-95db73790723
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bc3bb4e36582f01584c0b89a12d43874322c3190
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80838587"
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
| Класс \<>  | Класс по умолчанию находится в. Ниже перечислены допустимые значения для этой команды.</br>-IN: указывает класс Интернета.</br>-CHAOS: указывает класс Chaos.</br>-ХЕСИОД: указывает класс MIT Афина Хесиод.</br>-ANY: указывает любой из перечисленных выше подстановочных знаков. |
|   {Справка   |                                                                                                                                        ?}                                                                                                                                         |

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)