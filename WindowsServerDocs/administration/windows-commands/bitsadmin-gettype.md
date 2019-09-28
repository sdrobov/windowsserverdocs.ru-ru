---
title: bitsadmin gettype
description: Раздел команд Windows для **битсадмин GetType** — Извлекает тип задания для указанного задания.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bec16f04-3e95-4587-889e-3de6ad03c9c8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ca46cb813809621f4fa79b3265198206729a392c
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381339"
---
# <a name="bitsadmin-gettype"></a>bitsadmin gettype



Возвращает тип задания для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetType <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="remarks"></a>Примечания

Тип может быть СКАЧАН, отправлен, отправлен-REPLY или UNKNOWN.

## <a name="BKMK_examples"></a>Примеров

В следующем примере извлекается тип задания для задания с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /GetType myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)