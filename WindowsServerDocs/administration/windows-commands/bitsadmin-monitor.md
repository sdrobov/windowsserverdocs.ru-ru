---
title: bitsadmin monitor
description: Справочная статья по команде монитора битсадмин, которая отслеживает задания в очереди на перемещение, принадлежащие текущему пользователю.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2c424d27-e011-49c2-b579-a2c235467c39
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7ce08eccf46fc17086d216bc6797bec451ace7eb
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926499"
---
# <a name="bitsadmin-monitor"></a>bitsadmin monitor

Отслеживает задания в очереди на перемещение, принадлежащие текущему пользователю.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /monitor [/allusers] [/refresh <seconds>]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| /аллусерс | Необязательный элемент. Отслеживает задания для всех пользователей. Для использования этого параметра необходимо иметь права администратора. |
| /Refresh | Необязательный элемент. Обновляет данные через интервал, заданный параметром `<seconds>` . Интервал обновления по умолчанию составляет 5 секунд. Чтобы прервать обновление, нажмите клавиши CTRL + C. |

## <a name="examples"></a>Примеры

Для отслеживания очереди на перемещение заданий, принадлежащих текущему пользователю, и обновляет данные каждые 60 секунд.

```
bitsadmin /monitor /refresh 60
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
