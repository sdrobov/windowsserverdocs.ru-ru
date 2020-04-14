---
title: bitsadmin getfilestotal
description: Раздел команд Windows для **битсадмин жетфилестотал**, который извлекает количество файлов в указанном задании.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c5de113e-f29c-4cd3-9392-0e300018d516
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bad42a8bef57ca4c4a1411a12f20979e4a95d178
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850687"
---
# <a name="bitsadmin-getfilestotal"></a>bitsadmin getfilestotal

Извлекает количество файлов в указанном задании.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getfilestotal <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задания | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере извлекается число файлов, включаемых в задание с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /getfilestotal myDownloadJob
```

## <a name="see-also"></a>См. также

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
