---
title: bitsadmin getminretrydelay
description: Раздел команд Windows для **битсадмин жетминретриделай** . Получает время ожидания (в секундах), в течение которого служба останавливается после возникновения временной ошибки, прежде чем пытаться переместить файл.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 54f0abab-c129-40ed-a603-50f464d26011
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0a2bde6340034e48b97b4c86f48a3b2ef72560a5
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381553"
---
# <a name="bitsadmin-getminretrydelay"></a>bitsadmin getminretrydelay



Возвращает продолжительность времени в секундах, в течение которого служба ожидает после возникновения временной ошибки, прежде чем пытаться переместить файл.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetMinRetryDelay <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="BKMK_examples"></a>Примеров

В следующем примере извлекается Минимальная задержка повторных попыток для задания с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /GetMinRetryDelay myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)