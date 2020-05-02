---
title: добавить псевдоним
description: Справочный раздел по команде добавления псевдонима, который добавляет псевдонимы в среду псевдонима.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5fe12f5d-11e9-4f3d-b7f9-40b26c8685e5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 807981c3581eea328291f2389e08065edbd280d3
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719022"
---
# <a name="add-alias"></a>добавить псевдоним

Добавляет псевдонимы в среду псевдонима. Если используется без параметров, команда **Добавить псевдоним** отображает справку в командной строке. Псевдонимы сохраняются в файле метаданных и загружаются с помощью команды **Load Metadata** .

## <a name="syntax"></a>Синтаксис

```
add alias <AliasName> <AliasValue>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<AliasName>` | Указывает имя псевдонима. |
| `<AliasValue>` | Задает значение псевдонима. |
| `/?` | Отображение справки в командной строке. |

## <a name="examples"></a>Примеры

Чтобы получить список всех теней, включая их псевдонимы, введите:

```
list shadows all
```

В следующем фрагменте показана теневая копия, которой назначен псевдоним по умолчанию VSS_SHADOW_x.

```
* Shadow Copy ID = {ff47165a-1946-4a0c-b7f4-80f46a309278}
%VSS_SHADOW_1%
```

Чтобы назначить новый псевдоним с именем System1 для этой теневой копии, введите:

```
add alias System1 %VSS_SHADOW_1%
```

Кроме того, псевдоним можно назначить с помощью идентификатора теневой копии:

```
add alias System1 {ff47165a-1946-4a0c-b7f4-80f46a309278}
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [команда загрузки метаданных](load-metadata.md)
