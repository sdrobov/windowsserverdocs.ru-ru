---
title: bitsadmin cancel
description: Раздел команд Windows для **битсадмин Cancel**, который удаляет задание из очереди на перемещение и удаляет все временные файлы, связанные с заданием.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7374b544-6a16-4d3e-872c-dcf4c02ad89d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5c2bdeef824bc269671cc5ae926fb77cd5726c58
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850837"
---
# <a name="bitsadmin-cancel"></a>bitsadmin cancel

Удаляет задание из очереди на перемещение и удаляет все временные файлы, связанные с заданием.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /cancel <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| задания | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере из очереди обмена удаляется задание *мидовнлоаджоб* .

```
C:\>bitsadmin /cancel myDownloadJob
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)