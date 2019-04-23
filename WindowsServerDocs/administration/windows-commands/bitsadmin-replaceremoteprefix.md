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
ms.openlocfilehash: 3d3eba4f62842fa7f862cd4eaea6830e6a08397a
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59868135"
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

## <a name="BKMK_examples"></a>Примеры

В следующем примере изменяется все файлы в задание с именем *myDownloadJob* которого удаленный URL-адрес начинается с *http://stageserver* для *http://prodserver*.
```
C:\>bitsadmin /ReplaceRemotePrefix myDownloadJob http://stageserver http://prodserver
```

## <a name="additional-information"></a>Дополнительные сведения

[Ключ синтаксиса командной строки](command-line-syntax-key.md)