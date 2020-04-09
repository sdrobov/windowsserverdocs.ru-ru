---
title: bitsadmin reset
description: Раздел команд Windows для **битсадмин Reset**, который отменяет все задания в очереди на перемещение, принадлежащие текущему пользователю.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0e4f9d1d-072c-493f-8d7a-f6d713c3ef29
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ed1dcf9bce06af527ffb5b6a79d76d860d78450c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849797"
---
# <a name="bitsadmin-reset"></a>bitsadmin reset

Отменяет все задания в очереди на пересылку, принадлежащие текущему пользователю. > Не удается сбросить задания, созданные локальной системой. Вместо этого необходимо быть администратором и использовать планировщик заданий, чтобы запланировать эту команду как задачу с использованием учетных данных локальной системы.

> [!NOTE]
> В Битсадмин 1,5 и более ранних версиях при наличии прав администратора параметр/Reset будет отменять все задания в очереди. Кроме того, параметр/аллусерс не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /reset [/allusers]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| /аллусерс | Необязательно. Отменяет все задания в очереди, принадлежащие текущему пользователю. Для использования этого параметра необходимо иметь права администратора. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере отменяются все задания в очереди на перемещение для текущего пользователя.

```
C:\>bitsadmin /reset
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)