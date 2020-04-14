---
title: битсадмин жетмаксдовнлоадтиме
description: Раздел команд Windows для **битсадмин жетмаксдовнлоадтиме**, который получает время ожидания загрузки в секундах.
ms.prod: windows-servemr
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: cdce64f6-7125-489d-be3c-4af1dfc8c46a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8b6e4a45da76d5ba39edae151454ad7f28a74085
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850637"
---
# <a name="bitsadmin-getmaxdownloadtime"></a>битсадмин жетмаксдовнлоадтиме

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Возвращает время ожидания загрузки в секундах.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getmaxdownloadtime <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задания | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере возвращается максимальное время загрузки для задания с именем *мидовнлоаджоб* в секундах.

```
C:\>bitsadmin /getmaxdownloadtime myDownloadJob
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
