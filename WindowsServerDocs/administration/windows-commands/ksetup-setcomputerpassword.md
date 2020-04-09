---
title: 'ksetup: сеткомпутерпассворд'
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e307d8f6-3b93-4c24-ac04-f31549f7dc7d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3e65ea6e935d9fde9c23842755c36e418928dec7
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841377"
---
# <a name="ksetupsetcomputerpassword"></a>ksetup: сеткомпутерпассворд



Задает пароль для локального компьютера. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

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

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров

Измените пароль учетной записи компьютера на локальном компьютере с IPops897 на ИПОП $897!.
```
ksetup /setcomputerpassword IPop$897!
```

## <a name="additional-references"></a>Дополнительные материалы

-   [Ksetup](ksetup.md)
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)