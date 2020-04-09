---
title: bitsadmin setnoprogresstimeout
description: Раздел команд Windows для битсадмин сетнопрогресстимеаут, который задает время в секундах, в течение которого служба пытается переместить файл после возникновения временной ошибки.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7fac50d9-cc6b-46a4-a96f-fab751ee1756
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 544a6c73f29684bc4091ec05fa28016fbc718bb2
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849357"
---
# <a name="bitsadmin-setnoprogresstimeout"></a>bitsadmin setnoprogresstimeout

Задает период времени в секундах, в течение которого BITS пытается переместить файл после первой временной ошибки.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetNoProgressTimeout <Job> <TimeOutvalue>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|
|тимеаутвалуе|Число, представленное в секундах.|

## <a name="remarks"></a>Примечания

-   Интервал времени ожидания не выполняется, когда задание встречает временную ошибку.
-   Интервал времени ожидания останавливается или сбрасывается при успешном передаче байта данных.
-   Если интервал времени ожидания выполнения превышает *тимеаутвалуе*, задание помещается в неустранимую ошибку.

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере устанавливается значение времени ожидания "нет выполнения" для задания с именем *мидовнлоаджоб* равным 20 секундам.
```
C:\>bitsadmin /SetNoProgressTimeout myDownloadJob 20
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)