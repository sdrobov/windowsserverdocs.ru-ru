---
title: ksetup:setcomputerpassword
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e307d8f6-3b93-4c24-ac04-f31549f7dc7d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0679bb9ee429e05c7679411c5493bd21b530ef8e
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59831545"
---
# <a name="ksetupsetcomputerpassword"></a>ksetup:setcomputerpassword



Задает пароль для локального компьютера. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /setcomputerpassword <Password>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Пароль >|Введенный пароль используется для задания учетной записи компьютера на локальном компьютере.</br>Пароль можно задать только с помощью учетной записи с правами администратора. Пароль может составлять от 1 до 156 буквенно-цифровые или специальные символы.|

## <a name="remarks"></a>Примечания

Эта команда влияет только учетная запись компьютера.

Необходимо перезагрузить компьютер для изменения пароля вступили в силу.

Пароль учетной записи компьютера не отображается в реестре или в качестве выходных данных из **ksetup** команды.

## <a name="BKMK_Examples"></a>Примеры

Измените пароль учетной записи компьютера, на локальном компьютере из IPops897 на IPop$ 897!.
```
ksetup /setcomputerpassword IPop$897!
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ksetup](ksetup.md)
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)