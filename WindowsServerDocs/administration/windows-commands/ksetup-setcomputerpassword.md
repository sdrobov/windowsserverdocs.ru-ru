---
title: 'ksetup: сеткомпутерпассворд'
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e307d8f6-3b93-4c24-ac04-f31549f7dc7d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9cb0c2ee36ed85ddfb015a80e86198fe788f8474
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724582"
---
# <a name="ksetupsetcomputerpassword"></a>ksetup: сеткомпутерпассворд



Задает пароль для локального компьютера.

## <a name="syntax"></a>Синтаксис

```
ksetup /setcomputerpassword <Password>
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<> пароля|Использует указанный пароль для задания учетной записи компьютера на локальном компьютере.</br>Пароль можно задать только с помощью учетной записи с правами администратора. Пароль может содержать от 1 до 156 букв и специальных символов.|

## <a name="remarks"></a>Примечания

Эта команда влияет только на учетную запись компьютера.

Чтобы изменение пароля вступило в силу, необходимо перезагрузить компьютер.

Пароль учетной записи компьютера не отображается в реестре или в качестве выходных данных команды **ksetup** .

## <a name="examples"></a>Примеры

Измените пароль учетной записи компьютера на локальном компьютере с IPops897 на ИПОП $897!.
```
ksetup /setcomputerpassword IPop$897!
```

## <a name="additional-references"></a>Дополнительные ссылки

-   [Ksetup](ksetup.md)
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)