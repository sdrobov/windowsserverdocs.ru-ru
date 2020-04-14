---
title: bitsadmin list
description: Раздел команд Windows для **списка битсадмин**, в котором перечислены задания перемещения, принадлежащие текущему пользователю.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1416965e-e0e6-49cf-b1d4-b286d3cf8716
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1883da7bfa71a41952f6f67e25eca4dbbdd3353c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850327"
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
| /аллусерс | Необязательно. Выводит список заданий для всех пользователей. Для использования этого параметра необходимо иметь права администратора. |
| /verbose | Необязательно. Предоставляет подробные сведения о каждом задании. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере извлекаются сведения о заданиях, принадлежащих текущему пользователю.

```
C:\>bitsadmin /list
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)