---
title: bitsadmin setnotifyflags
description: Раздел команд Windows для **битсадмин сетнотифифлагс**, который задает флаги уведомления о событиях для указанного задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d5763d95-94a6-45ca-9e03-891c20047e06
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 73c088ce2bae8d2ad99b313417c14449ddd822b5
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81122790"
---
# <a name="bitsadmin-setnotifyflags"></a>bitsadmin setnotifyflags

Задает флаги уведомления о событии для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /setnotifyflags <job> <notifyflags>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| задания | Отображаемое имя задания или идентификатор GUID. |
| нотифифлагс | Может включать один или несколько следующих флагов уведомлений, в том числе:<ul><li>**1.** создает событие, когда все файлы в задании были переданы.</li><li>**2.** создает событие при возникновении ошибки.</li><li>**3.** формирует событие, когда все файлы завершили перенос или при возникновении ошибки.</li><li>**4.** отключает уведомления.</li></ul> |

## <a name="examples"></a>Примеры

В следующем примере устанавливаются флаги уведомления для создания события при возникновении ошибки для задания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /setnotifyflags myDownloadJob 2
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)