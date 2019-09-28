---
title: bitsadmin getnotifyflags
description: Раздел команд Windows для **битсадмин жетнотифифлагс** — Получает флаги уведомления для указанного задания.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d4657e6c-8959-4db7-a4af-e73d3f80ecf8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 56ee3a30050b6cc934b35bab24e9508911ea250e
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381478"
---
# <a name="bitsadmin-getnotifyflags"></a>bitsadmin getnotifyflags



Возвращает флаги уведомления для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetNotifyFlags <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="remarks"></a>Примечания

Задание может содержать один или несколько следующих флагов уведомления.

|-----|-----| | 0x001 | Создавать событие при передаче всех файлов в задании. | | 0x002 | Создавать событие при возникновении ошибки. | | 0x004 | Отключить уведомления. | | 0x008 | Создавать событие, когда задание изменяется или выполняется перенос. |

## <a name="BKMK_examples"></a>Примеров

В следующем примере извлекаются флаги уведомления для задания с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /GetNotifyFlags myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)