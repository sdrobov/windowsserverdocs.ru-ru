---
title: bitsadmin getcompletiontime
description: Раздел команд Windows для **битсадмин жеткомплетионтиме**, который получает время завершения передачи данных заданием.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7a4b3c1c-9832-4724-86b2-cce3c01bfa28
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5408e7e8c35135601a4a0af0ab7e9c55cea4c8dd
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850757"
---
# <a name="bitsadmin-getcompletiontime"></a>bitsadmin getcompletiontime

Возвращает время, когда задание завершило передачу данных.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getcompletiontime <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задания | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере извлекается время, когда задание с именем *мидовнлоаджоб* завершило передачу данных.

```
C:\>bitsadmin /getcompletiontime myDownloadJob
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)