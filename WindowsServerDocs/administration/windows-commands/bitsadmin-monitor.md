---
title: bitsadmin monitor
description: Раздел команд Windows для **монитора битсадмин**, который отслеживает задания в очереди на перемещение, принадлежащие текущему пользователю.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2c424d27-e011-49c2-b579-a2c235467c39
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bda268afd5fda24bba2afb04b32bac9cda9a05bb
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850217"
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
| /аллусерс | Необязательно. Отслеживает задания для всех пользователей. Для использования этого параметра необходимо иметь права администратора. |
| /Refresh | Необязательно. Обновляет данные с интервалом, заданным параметром `<seconds>`. Интервал обновления по умолчанию составляет 5 секунд. Чтобы прервать обновление, нажмите клавиши CTRL + C. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере производится мониторинг очереди на перемещение заданий, принадлежащих текущему пользователю, и обновление данных каждые 60 секунд.

```
C:\>bitsadmin /monitor /refresh 60
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)