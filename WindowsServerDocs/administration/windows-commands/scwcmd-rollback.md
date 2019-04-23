---
title: Scwcmd отката
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4fd9f89b-0420-420a-ad20-4a328636b1e7
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6d6cd79c7068d86915141a37b5a4510bddefc94c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59852205"
---
# <a name="scwcmd-rollback"></a>Scwcmd: rollback

> Область применения. Windows Server 2012 R2, Windows Server 2012

Применяет самые последние доступные политику отката, а затем удаляет эту политику отката.

## <a name="syntax"></a>Синтаксис

```
scwcmd rollback /m:<ComputerName> [/u:<UserName>] [/pw:<Password>]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/ m:\<имя_компьютера >|Указывает NetBIOS-имя, DNS-имя или IP-адрес компьютера, где должна выполняться операция отката.|
|/u:\<UserName>|Указывает альтернативную учетную запись пользователя для использования при выполнении удаленного отката. По умолчанию используется вошедшего пользователя.|
|/ PW:\<пароль >|Указывает учетные данные другого пользователя, для использования при удаленного отката. По умолчанию используется вошедшего пользователя.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

Scwcmd.exe доступна только на компьютерах под управлением Windows Server 2008 R2, Windows Server 2008 или Windows Server 2003.

## <a name="BKMK_Examples"></a>Примеры

Чтобы откатить политику безопасности на компьютере с IP-адресом 172.16.0.0, введите следующую команду:
```
scwcmd rollback /m:172.16.0.0
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)