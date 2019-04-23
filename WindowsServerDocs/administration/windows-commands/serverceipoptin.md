---
title: serverceipoptin
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3d7d7fa7-0689-4797-b802-36fe260d21a0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fca2497af308faf298e1df03d8b07c68bf9e8b98
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59840565"
---
# <a name="serverceipoptin"></a>serverceipoptin

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Позволяет участвовать в программе улучшения качества клиента (CEIP).
## <a name="syntax"></a>Синтаксис
```
serverceipoptin [/query] [/enable] [/disable]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/ Query|Проверяет текущее значение параметра.|
|/ Enable|Активирует участие.|
|/ Disable|Отключает участие.|
|/?|Отображение справки в командной строке.|
## <a name="BKMK_Examples"></a>Примеры
Чтобы проверить текущие параметры, введите следующую команду:
```
serverceipoptin /query
```
Чтобы включить участие, введите следующую команду:
```
serverceipoptin /enable
```
Чтобы отказаться от участия, введите:
```
serverceipoptin /disable
```
## <a name="additional-references"></a>Дополнительные ссылки
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)

