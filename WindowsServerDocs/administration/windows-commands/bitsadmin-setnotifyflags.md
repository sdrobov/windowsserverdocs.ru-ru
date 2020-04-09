---
title: bitsadmin setnotifyflags
description: Раздел команд Windows для битсадмин сетнотифифлагс, который задает флаги уведомления о событиях для указанного задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d5763d95-94a6-45ca-9e03-891c20047e06
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fd3001fa4ae7f51cab92556f4f2f498511cca5ae
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849287"
---
# <a name="bitsadmin-setnotifyflags"></a>bitsadmin setnotifyflags

Задает флаги уведомления о событии для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetNotifyFlags <Job> <NotifyFlags>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|
|нотифифлагс|См. примечания|

## <a name="remarks"></a>Примечания

Параметр **нотифифлагс** может содержать один или несколько следующих флагов уведомления.

|-----|-----| | 1 | Создавать событие при передаче всех файлов в задании. | | 2 | Создавать событие при возникновении ошибки. | | 4 | Отключить уведомления. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере задается задание notify flags для события "передано" и "ошибка" для задания с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /SetNotifyFlags myDownloadJob 3
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)