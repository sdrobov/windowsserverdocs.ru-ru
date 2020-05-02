---
title: serverceipoptin
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3d7d7fa7-0689-4797-b802-36fe260d21a0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7d4214b9105e04f355bd6e09aeb7bc671ae6007d
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721968"
---
# <a name="serverceipoptin"></a>serverceipoptin

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

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
|/?|Отображение справки в командной строке.|
## <a name="examples"></a>Примеры
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
## <a name="additional-references"></a>Дополнительные ссылки
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

