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
ms.openlocfilehash: 848c57736c3530e296cffb970237149b4634de67
ms.sourcegitcommit: d84dc3d037911ad698f5e3e84348b867c5f46ed8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2019
ms.locfileid: "66266514"
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