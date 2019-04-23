---
title: bitsadmin setnotifyflags
description: Раздел Windows команды для **bitsadmin setnotifyflags** -задает событие флаги уведомления для указанного задания.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d5763d95-94a6-45ca-9e03-891c20047e06
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bc817e03e0f1916ea392830d14985a7a1377d69a
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59868795"
---
# <a name="bitsadmin-setnotifyflags"></a>bitsadmin setnotifyflags

Задает событие флаги уведомления для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetNotifyFlags <Job> <NotifyFlags>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|
|NotifyFlags|См. в разделе "Примечания"|

## <a name="remarks"></a>Примечания

**NotifyFlags** параметр может содержать один или несколько из следующих флагов уведомлений.

|---|---| | 1 | Создать событие, когда все файлы в задании были перенесены. | | 2 | Создавать событие при возникновении ошибки. | | 4 | Отключение уведомлений. |

## <a name="BKMK_examples"></a>Примеры

Следующий пример устанавливает флаги уведомления для передана и события ошибок заданий для задания с именем *myDownloadJob*.
```
C:\>bitsadmin /SetNotifyFlags myDownloadJob 3
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)