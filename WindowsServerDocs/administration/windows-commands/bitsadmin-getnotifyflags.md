---
title: bitsadmin getnotifyflags
description: Раздел команд Windows для **битсадмин жетнотифифлагс**, который получает флаги уведомления для указанного задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d4657e6c-8959-4db7-a4af-e73d3f80ecf8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3138baea05f793cfb587d3f8fb669d446daea6b5
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850587"
---
# <a name="bitsadmin-getnotifyflags"></a>bitsadmin getnotifyflags

Возвращает флаги уведомления для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getnotifyflags <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задания | Отображаемое имя задания или идентификатор GUID. |

## <a name="remarks"></a>Примечания

Задание может содержать один или несколько следующих флагов уведомления:

| Flag | Описание |
| ----- | ----- |
| 0x001 | Создавать событие, когда все файлы в задании были переданы. |
| 0x002 | Создавать событие при возникновении ошибки. |
| 0x004 | Отключение уведомлений. |
| 0x008 | Создание события при изменении или переносе задания. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере извлекаются флаги уведомления для задания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /getnotifyflags myDownloadJob
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)