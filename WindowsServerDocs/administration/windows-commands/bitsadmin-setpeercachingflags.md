---
title: bitsadmin setpeercachingflags
description: Раздел Windows команды для **bitsadmin setpeercachingflags** -задает флаги, определяющие, если файлы задания можно кэшировать и обслуживать одноранговых узлов, и если задание можно загрузить с одноранговых узлов.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3f54a127-fb68-49a5-b843-664ec833df67
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2d50a6ccd83a6251808ca3d66437e52f641c60a7
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59814255"
---
# <a name="bitsadmin-setpeercachingflags"></a>bitsadmin setpeercachingflags



Задает флаги, определяющие, если файлы задания можно кэшировать и обслуживать одноранговых узлов, и если задание можно загрузить содержимое из одноранговых узлов.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetPeerCachingFlags <Job> <value> 
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|
|Значение|Значение — целое число без знака с следующую интерпретацию битам в двоичное представление.</br>1 - задание можно загрузить содержимое из одноранговых узлов.</br>2 - файлы задания можно кэшировать и обслуживать одноранговых узлов.|

## <a name="BKMK_examples"></a>Примеры

Следующий пример устанавливает флаги для задания с именем *myJob* позволит загружать содержимое из одноранговых узлов.
```
C:\>bitsadmin / SetPeerCachingFlags myJob 1 
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)