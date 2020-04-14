---
title: bitsadmin getminretrydelay
description: Раздел команд Windows для **битсадмин жетминретриделай**, который получает время ожидания службы в секундах после возникновения временной ошибки перед попыткой перемещения файла.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 54f0abab-c129-40ed-a603-50f464d26011
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d79ffdf1f45b0198b4af535ed83154c3c2ec24f4
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850627"
---
# <a name="bitsadmin-getminretrydelay"></a>bitsadmin getminretrydelay

Возвращает продолжительность времени в секундах, в течение которого служба будет ожидать после возникновения временной ошибки, прежде чем пытаться переместить файл.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getminretrydelay <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задания | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере извлекается Минимальная задержка повторных попыток для задания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /getminretrydelay myDownloadJob
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)