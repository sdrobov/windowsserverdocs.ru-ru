---
title: bitsadmin getnotifyflags
description: Раздел Windows команды для **bitsadmin getnotifyflags** -извлекает флаги уведомления для указанного задания.
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 690e94805c5e61d96603e4ade102fb3a4bda409e
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59889285"
---
# <a name="bitsadmin-getnotifyflags"></a>bitsadmin getnotifyflags



Извлекает флаги уведомления для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetNotifyFlags <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|

## <a name="remarks"></a>Примечания

Задание может содержать один или несколько из следующих флагов уведомлений.

|---|---| | 0x001 | Создать событие, когда все файлы в задании были перенесены. | | 0x002 | Создавать событие при возникновении ошибки. | | 0x004 | Отключение уведомлений. | | 0x008 | Создавать событие при изменении задания или хода передачи. |

## <a name="BKMK_examples"></a>Примеры

В следующем примере извлекается флаги уведомления задания с именем *myDownloadJob*.
```
C:\>bitsadmin /GetNotifyFlags myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)