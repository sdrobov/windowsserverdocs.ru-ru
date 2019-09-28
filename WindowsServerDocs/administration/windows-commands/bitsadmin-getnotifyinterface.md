---
title: bitsadmin getnotifyinterface
description: Раздел команд Windows для **битсадмин жетнотифинтерфаце** . определяет, зарегистрировал ли другая программа интерфейс обратного вызова com для указанного задания.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 40bf9dd8-b167-406a-80a6-a5a6f1b8cf7f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 826e13cf8a3e54935ceb5a72ff82647cacfc3be5
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381475"
---
# <a name="bitsadmin-getnotifyinterface"></a>bitsadmin getnotifyinterface

Определяет, зарегистрировал ли другая программа интерфейс обратного вызова COM (интерфейс уведомления) для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetNotifyInterface <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="remarks"></a>Примечания

Отображает ЗАРЕГИСТРИРОВАНные или отмененные регистрации.

> [!NOTE]
> Невозможно определить программу, которая зарегистрировала интерфейс обратного вызова.

## <a name="BKMK_examples"></a>Примеров

В следующем примере извлекается интерфейс notify для задания с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /GetNotifyInterface myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)