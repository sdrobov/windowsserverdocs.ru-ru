---
title: 'ksetup: думпстате'
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3ef2f7b8-97af-4f42-9542-cff324840637
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 46f827d26d867392db4cbef92cf5be496aee8d74
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841517"
---
# <a name="ksetupdumpstate"></a>ksetup: думпстате



Отображает текущее состояние параметров области для всех областей, определенных на компьютере. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /dumpstate
```

#### <a name="parameters"></a>Параметры

Нет

## <a name="remarks"></a>Примечания

Выходные данные этой команды включают область по умолчанию (домен, членом которого является компьютер) и все сферы, определенные на этом компьютере. Для каждой области предусмотрено следующее:
-   Все центры распределения ключей (Кдкс), связанные с этой областью
-   Все флаги **области набора** для этой области
-   Пароль KDC

Эта команда не отображает имя домена, указанное при обнаружении DNS, или командой **ksetup/Domain**.

Эта команда не отображает пароль компьютера, заданный с помощью команды **ksetup/сеткомпутерпассворд**.

**Ksetup** создает те же выходные данные, что и **Ksetup/думпстате**.

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров

Поиск большинства конфигураций области Kerberos на компьютере:
```
ksetup /dumpstate
```

## <a name="additional-references"></a>Дополнительные материалы

-   [Ksetup](ksetup.md)
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)