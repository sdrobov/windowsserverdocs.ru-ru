---
title: bitsadmin getdisplayname
description: Раздел Windows команды для **bitsadmin getdisplayname** -извлекает отображаемое имя указанного задания.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e5c0e76c-4cc6-42d8-ac30-30bf3dc11b9b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c1ef16f54b7b825e4293a3870d8181985b83843b
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59857605"
---
# <a name="bitsadmin-getdisplayname"></a>bitsadmin getdisplayname



Получает отображаемое имя указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetDisplayName <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|

## <a name="BKMK_examples"></a>Примеры

В следующем примере извлекается отображаемое имя для задания с именем *myDownloadJob*.
```
C:\>bitsadmin /GetDisplayName myDownloadJob
```
Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)