---
title: ksetup думпстате
description: Справочный раздел по ksetup думпстате коммнанд, который отображает текущее состояние параметров области для всех областей, определенных на компьютере.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3ef2f7b8-97af-4f42-9542-cff324840637
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4ccb75ac143239d97b823fb7030f9a8020b4b4f6
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83817744"
---
# <a name="ksetup-dumpstate"></a>ksetup думпстате

Отображает текущее состояние параметров области для всех областей, определенных на компьютере. Эта команда отображает те же выходные данные, что и команда **ksetup** .

## <a name="syntax"></a>Синтаксис

```
ksetup /dumpstate
```

### <a name="remarks"></a>Remarks

- Выходные данные этой команды включают область по умолчанию (домен, членом которого является компьютер) и все сферы, определенные на этом компьютере. Для каждой области предусмотрено следующее:

  - Все центры распределения ключей (Кдкс), связанные с этой областью.

  - Все флаги **области набора** для этой области.

  - Пароль KDC.

- Эта команда не отображает имя домена, указанное при обнаружении DNS или командой `ksetup /domain` .

- Эта команда не отображает пароль компьютера, установленный с помощью команды `ksetup /setcomputerpassword` .

## <a name="examples"></a>Примеры

Чтобы выбрать конфигурацию области Kerberos на компьютере, введите:

```
ksetup /dumpstate
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда ksetup](ksetup.md)