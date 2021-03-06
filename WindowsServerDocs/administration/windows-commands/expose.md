---
title: expose
description: Справочная статья по команде предоставления, которая предоставляет постоянную теневую копию в виде буквы диска, общего ресурса или точки подключения.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9b0a21cf-3bef-4ade-b8f1-ac42f9203947
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 816aad0ba57a30d9d3a05709941b1915d9a97d03
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85932399"
---
# <a name="expose"></a>expose

Предоставляет постоянную теневую копию в виде буквы диска, общего ресурса или точки подключения.

## <a name="syntax"></a>Синтаксис

```
expose <shadowID> {<drive:> | <share> | <mountpoint>}
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| шадовид | Указывает теневой идентификатор теневой копии, которую необходимо предоставить. Можно также использовать существующий псевдоним или переменную среды вместо *шадовид*. Чтобы просмотреть существующие псевдонимы, используйте параметр **Добавить** без параметров. |
| `<drive:>` | Предоставляет указанную теневую копию в виде буквы диска (например, `p:` ). |
| `<share>` | Предоставляет указанную теневую копию в общей папке (например, `\\machinename` ).   |
| `<mountpoint>` | Предоставляет указанную теневую копию точке подключения (например, `C:\shadowcopy` ). |

### <a name="examples"></a>Примеры

Чтобы предоставить устойчивую теневую копию, связанную с переменной среды VSS_SHADOW_1, в качестве диска X, введите:

```
expose %vss_shadow_1% x:
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Diskshadow, команда](diskshadow.md)
