---
title: BdeHdCfg невдривелеттер
description: Раздел команд Windows для **BdeHdCfg невдривелеттер**, который назначает новую букву диска части диска, используемой в качестве системного диска.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f1f200a0-6850-4f0d-9047-f9f982a590f8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4a8757e7d0684912525817708fbe34953b049582
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851057"
---
# <a name="bdehdcfg-newdriveletter"></a>BdeHdCfg: невдривелеттер

Назначает новую букву диска части диска, используемой в качестве системного диска. Пример того, как можно использовать эту команду, см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
bdehdcfg -target {default|unallocated|<DriveLetter> shrink|<DriveLetter> merge} -newdriveletter <DriveLetter>
```

#### <a name="parameters"></a>Параметры

| Параметр | Описание |
| ---------| ----------- |
|`<DriveLetter>`|Определяет букву диска, которая будет назначена указанному целевому диску.|

## <a name="remarks"></a>Примечания

Рекомендуется не назначать диску букву диска системному накопителю.

## <a name="examples"></a><a name="BKMK_Examples"></a>Примеров

В следующем примере показано, что диску по умолчанию назначается буква P.

```
bdehdcfg -target default -newdriveletter P:
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [BdeHdCfg](bdehdcfg.md)