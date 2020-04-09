---
title: bitsadmin getdisplayname
description: Раздел команд Windows для **битсадмин. DisplayName**, который извлекает отображаемое имя указанного задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e5c0e76c-4cc6-42d8-ac30-30bf3dc11b9b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6944dc2b7a63ca986fb285d26796f350c1052295
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850717"
---
# <a name="bitsadmin-getdisplayname"></a>bitsadmin getdisplayname

Извлекает отображаемое имя указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getdisplayname <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задания | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере извлекается отображаемое имя для задания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /getdisplayname myDownloadJob
```

## <a name="additional-references"></a>Дополнительная справка

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)