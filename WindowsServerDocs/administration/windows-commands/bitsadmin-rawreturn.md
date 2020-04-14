---
title: bitsadmin rawreturn
description: Раздел команд Windows для **битсадмин равретурн**, который возвращает данные, подходящие для синтаксического анализа.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bbe97130-26f6-4cdd-84f1-baf530ce38b7
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e8cd84b6082b1fda8061ee7b324dd66991d3b206
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849887"
---
# <a name="bitsadmin-rawreturn"></a>bitsadmin rawreturn

Возвращает данные, подходящие для синтаксического анализа. Как правило, эта команда используется совместно с параметрами **/CREATE** и **/Get*** для получения только значения. Этот параметр необходимо указать перед другими коммутаторами.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /rawreturn
```

## <a name="remarks"></a>Примечания

- Удаляет символы новой строки и форматирование из выходных данных.

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере извлекаются необработанные данные для состояния задания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /rawreturn /getstate myDownloadJob
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)