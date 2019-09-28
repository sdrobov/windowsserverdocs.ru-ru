---
title: 'ksetup: думпстате'
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 625d05b2fea9ae58681648c64e309aa8b2a201ed
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71374995"
---
# <a name="ksetupdumpstate"></a>ksetup: думпстате



Отображает текущее состояние параметров области для всех областей, определенных на компьютере. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /dumpstate
```

### <a name="parameters"></a>Параметры

Нет

## <a name="remarks"></a>Примечания

Выходные данные этой команды включают область по умолчанию (домен, членом которого является компьютер) и все сферы, определенные на этом компьютере. Для каждой области предусмотрено следующее:
-   Все центры распределения ключей (Кдкс), связанные с этой областью
-   Все флаги **области набора** для этой области
-   Пароль KDC

Эта команда не отображает имя домена, указанное при обнаружении DNS, или командой **ksetup/Domain**.

Эта команда не отображает пароль компьютера, заданный с помощью команды **ksetup/сеткомпутерпассворд**.

**Ksetup** создает те же выходные данные, что и **Ksetup/думпстате**.

## <a name="BKMK_Examples"></a>Примеров

Поиск большинства конфигураций области Kerberos на компьютере:
```
ksetup /dumpstate
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ksetup](ksetup.md)
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)