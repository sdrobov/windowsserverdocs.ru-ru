---
title: bitsadmin list
description: Справочная статья по команде битсадмин List, в которой перечислены задания перемещения, принадлежащие текущему пользователю.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1416965e-e0e6-49cf-b1d4-b286d3cf8716
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9d9a2c86536ff0910b4e0a8bea15ec43d9371087
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926554"
---
# <a name="bitsadmin-list"></a>bitsadmin list

Список заданий перемещения, принадлежащих текущему пользователю.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /list [/allusers][/verbose]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| /аллусерс | Необязательный элемент. Выводит список заданий для всех пользователей. Для использования этого параметра необходимо иметь права администратора. |
| /verbose | Необязательный элемент. Предоставляет подробные сведения о каждом задании. |

## <a name="examples"></a>Примеры

Для получения сведений о заданиях, принадлежащих текущему пользователю.

```
bitsadmin /list
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
