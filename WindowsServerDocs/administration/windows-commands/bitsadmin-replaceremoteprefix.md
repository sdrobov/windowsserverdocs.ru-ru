---
title: bitsadmin replaceremoteprefix
description: Раздел Windows команды для **bitsadmin replaceremoteprefix** -все файлы в задание удаленного URL-адрес которых начинается с *OldPrefix* будут изменены для использования *NewPrefix*.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d0e0abb1-bdb4-4c74-abbc-16c809f5fd81
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 25c0f997ea0b9f97051baa291bdf87c84b6b1cbb
ms.sourcegitcommit: 6ef4986391607bb28593852d06cc6645e548a4b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66811298"
---
# <a name="bitsadmin-replaceremoteprefix"></a>bitsadmin replaceremoteprefix

Все файлы в задание удаленного URL-адрес которых начинается с *OldPrefix* будут изменены для использования *NewPrefix*.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /ReplaceRemotePrefix <Job> <OldPrefix> <NewPrefix
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|
|OldPrefix|Существующие префикс URL-адреса|
|NewPrefix|Новый префикс URL-адреса|

## <a name="examples"></a>Примеры

В следующем примере изменяется все файлы в задание с именем *myDownloadJob* которого удаленный URL-адрес начинается с *http://stageserver* для *http://prodserver* .

```
C:\>bitsadmin /ReplaceRemotePrefix myDownloadJob http://stageserver http://prodserver
```

## <a name="additional-information"></a>Дополнительные сведения

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)