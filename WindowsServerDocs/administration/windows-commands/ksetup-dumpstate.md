---
title: 'ksetup: думпстате'
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3ef2f7b8-97af-4f42-9542-cff324840637
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 27a7e3154b9dfa663b88b04857ea7650995613c6
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724643"
---
# <a name="ksetupdumpstate"></a>ksetup: думпстате



Отображает текущее состояние параметров области для всех областей, определенных на компьютере.

## <a name="syntax"></a>Синтаксис

```
ksetup /dumpstate
```

#### <a name="parameters"></a>Параметры

None

## <a name="remarks"></a>Примечания

Выходные данные этой команды включают область по умолчанию (домен, членом которого является компьютер) и все сферы, определенные на этом компьютере. Для каждой области предусмотрено следующее:
-   Все центры распределения ключей (Кдкс), связанные с этой областью
-   Все флаги **области набора** для этой области
-   Пароль KDC

Эта команда не отображает имя домена, указанное при обнаружении DNS, или командой **ksetup/Domain**.

Эта команда не отображает пароль компьютера, заданный с помощью команды **ksetup/сеткомпутерпассворд**.

**Ksetup** создает те же выходные данные, что и **Ksetup/думпстате**.

## <a name="examples"></a>Примеры

Поиск большинства конфигураций области Kerberos на компьютере:
```
ksetup /dumpstate
```

## <a name="additional-references"></a>Дополнительные ссылки

-   [Ksetup](ksetup.md)
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)