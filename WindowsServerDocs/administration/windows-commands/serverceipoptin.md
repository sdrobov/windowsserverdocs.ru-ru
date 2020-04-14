---
title: serverceipoptin
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3d7d7fa7-0689-4797-b802-36fe260d21a0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c0625694053a2d673cd86e12d6f6d54662a6c81d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80834683"
---
# <a name="serverceipoptin"></a>serverceipoptin

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Позволяет участвовать в программа улучшения качества программного обеспечения (CEIP).
## <a name="syntax"></a>Синтаксис
```
serverceipoptin [/query] [/enable] [/disable]
```
#### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/Query|проверяет текущее значение параметра.|
|разрешение|Включает участие.|
|/Disable|Отключает участие.|
|/?|Отображает справку в командной строке.|
## <a name="examples"></a><a name=BKMK_Examples></a>Примеров
Чтобы проверить текущие параметры, введите:
```
serverceipoptin /query
```
Чтобы включить участие, введите:
```
serverceipoptin /enable
```
Чтобы отключить участие, введите:
```
serverceipoptin /disable
```
## <a name="additional-references"></a>Дополнительные материалы
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

