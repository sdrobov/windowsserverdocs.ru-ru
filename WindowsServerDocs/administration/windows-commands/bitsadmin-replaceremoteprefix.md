---
title: bitsadmin replaceremoteprefix
description: Раздел команд Windows для **битсадмин реплацеремотепрефикс**, при необходимости изменяется удаленный URL-адрес для всех файлов в задании с *олдпрефикс* на *невпрефикс*.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d0e0abb1-bdb4-4c74-abbc-16c809f5fd81
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0cea0108a292815e31e893e91dc4079305c1da9a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849817"
---
# <a name="bitsadmin-replaceremoteprefix"></a>bitsadmin replaceremoteprefix

При необходимости изменяет удаленный URL-адрес для всех файлов в задании с *олдпрефикс* на *невпрефикс*.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /replaceremoteprefix <job> <oldprefix> <newprefix>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задания | Отображаемое имя задания или идентификатор GUID. |
| олдпрефикс | Существующий префикс URL-адреса. |
| невпрефикс | Новый префикс URL-адреса. |

## <a name="examples"></a>Примеры

В следующем примере изменяется удаленный URL-адрес для всех файлов в задании с именем *мидовнлоаджоб*, от *http://stageserver* до *http://prodserver* .

```
C:\>bitsadmin /replaceremoteprefix myDownloadJob http://stageserver http://prodserver
```

## <a name="additional-information"></a>Дополнительные сведения

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)