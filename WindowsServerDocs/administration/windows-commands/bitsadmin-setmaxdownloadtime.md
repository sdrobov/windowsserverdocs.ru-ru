---
title: битсадмин сетмаксдовнлоадтиме
description: Раздел команд Windows для битсадмин сетмаксдовнлоадтиме, который задает время ожидания загрузки в секундах.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 16b96cf1-5738-415c-9b9d-c4ea8d5e4fec
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fd44011cd14d575a9c3798ede45641fac4c3dc75
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849377"
---
# <a name="bitsadmin-setmaxdownloadtime"></a>битсадмин сетмаксдовнлоадтиме

Задает время ожидания загрузки в секундах.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetMaxDownloadTime <Job> <Timeout>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|
|Время ожидания|Время ожидания в секундах|

## <a name="remarks"></a>Примечания

-   Н/Д

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере задается время ожидания для задания с именем *мидовнлоаджоб* равным 10 секундам.
```
C:\>bitsadmin /SetMaxDownloadTime myDownloadJob 10
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)