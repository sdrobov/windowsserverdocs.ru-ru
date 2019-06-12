---
title: bitsadmin getpeercachingflags
description: Раздел Windows команды для **bitsadmin getpeercachingflags** -извлекает флаги, определяющие файлы задания можно кэшировать и обслуживать одноранговых узлов, если бит можно загрузить содержимое для задания от одноранговых узлов.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3c3c9f28-4c04-4c49-a23a-dee5bbcc8981
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 28f248bab3e3cc3f5c7dd4f5f878f0b6d776029b
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66434926"
---
# <a name="bitsadmin-getpeercachingflags"></a>bitsadmin getpeercachingflags

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Получает флаги, определяющие файлы задания можно кэшировать и обслуживать одноранговых узлов, если бит можно загрузить содержимое для задания от одноранговых узлов.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetPeerCachingFlags <Job> 
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------|--------|
|Job|Отображаемое имя или идентификатор GUID задания|

## <a name="BKMK_examples"></a>Примеры
В следующем примере извлекается флаги для задания с именем *myJob*.

```
C:\>bitsadmin /GetPeerCachingFlags myJob
```

## <a name="additional-references"></a>Дополнительные ссылки
[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)


