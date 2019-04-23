---
title: ksetup:dumpstate
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3ef2f7b8-97af-4f42-9542-cff324840637
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8e5e8f20188fc27cc08dfd37c5fdbd811925f476
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59863125"
---
# <a name="ksetupdumpstate"></a>ksetup:dumpstate



Отображает текущее состояние области параметров для всех областей, которые определены на компьютере. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /dumpstate
```

### <a name="parameters"></a>Параметры

Нет

## <a name="remarks"></a>Примечания

Выходные данные этой команды включают область по умолчанию (домен, что компьютер является членом) и все области, которые определены на этом компьютере. Ниже приведен для каждой области.
-   Все ключ центры распространения (KDC), которые связаны с этой области
-   Все **область набора** флаги для этой области
-   Пароль KDC

Эта команда не отображает имя домена, который указан с обнаружением DNS или с помощью команды **/Domain ksetup**.

Эта команда не отображает пароль компьютера, который задается с помощью команды **ksetup /setcomputerpassword**.

**Ksetup** создает тот же вывод, как **ksetup /dumpstate**.

## <a name="BKMK_Examples"></a>Примеры

Найти большинство конфигураций сферы Kerberos на компьютере:
```
ksetup /dumpstate
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ksetup](ksetup.md)
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)