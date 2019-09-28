---
title: bitsadmin setnotifyflags
description: Раздел команд Windows для **битсадмин сетнотифифлагс** — устанавливает флаги уведомления о событиях для указанного задания.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: d9cfabf05610cbbe8fa65fd16b0d33e161dcef9b
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380452"
---
# <a name="bitsadmin-setnotifyflags"></a>bitsadmin setnotifyflags

Задает флаги уведомления о событии для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetNotifyFlags <Job> <NotifyFlags>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|
|нотифифлагс|См. примечания|

## <a name="remarks"></a>Примечания

Параметр **нотифифлагс** может содержать один или несколько следующих флагов уведомления.

|-----|-----| | 1 | Создавать событие при передаче всех файлов в задании. | | 2 | Создавать событие при возникновении ошибки. | | 4 | Отключить уведомления. |

## <a name="BKMK_examples"></a>Примеров

В следующем примере задается задание notify flags для события "передано" и "ошибка" для задания с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /SetNotifyFlags myDownloadJob 3
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)