---
title: 'ksetup: сеткомпутерпассворд'
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: d1d3742476385eb770c9cb5c798c1f6ab27c74f8
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71374945"
---
# <a name="ksetupsetcomputerpassword"></a>ksetup: сеткомпутерпассворд



Задает пароль для локального компьютера. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /setcomputerpassword <Password>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|@no__t 0Password >|Использует указанный пароль для задания учетной записи компьютера на локальном компьютере.</br>Пароль можно задать только с помощью учетной записи с правами администратора. Пароль может содержать от 1 до 156 букв и специальных символов.|

## <a name="remarks"></a>Примечания

Эта команда влияет только на учетную запись компьютера.

Чтобы изменение пароля вступило в силу, необходимо перезагрузить компьютер.

Пароль учетной записи компьютера не отображается в реестре или в качестве выходных данных команды **ksetup** .

## <a name="BKMK_Examples"></a>Примеров

Измените пароль учетной записи компьютера на локальном компьютере с IPops897 на ИПОП $897!.
```
ksetup /setcomputerpassword IPop$897!
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ksetup](ksetup.md)
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)