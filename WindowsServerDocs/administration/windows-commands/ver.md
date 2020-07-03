---
title: ver
description: Справочная статья по версии ver, в которой отображается номер операционной системы.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5a9c6cd4-b67d-4b30-8c56-5f9798eafd2a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bd9b40fa526c2917b6cdcbc8d54da510eb40bc53
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85931339"
---
# <a name="ver"></a>ver



Отображает номер версии операционной системы.

Эта команда поддерживается в командной строке Windows (Cmd.exe), но не в PowerShell.



## <a name="syntax"></a>Синтаксис

```
ver
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/?|Отображение справки в командной строке.|

## <a name="examples"></a>Примеры

Чтобы получить номер версии операционной системы из командной оболочки (cmd.exe), введите:

```
ver
```

Команда ver не работает в PowerShell. Чтобы получить версию ОС из PowerShell, введите:

```powershell
$PSVersionTable.BuildVersion
````


## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
