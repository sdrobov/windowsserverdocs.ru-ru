---
title: bitsadmin кэширования и getconfigurationflags
description: Раздел Windows команды для **bitsadmin кэширования и getconfigurationflags** - получает конфигурацию флаги, определяющие, если компьютер обслуживает содержимое для одноранговых узлов и можно загрузить содержимое из одноранговых узлов.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 124ddc15-3444-4bd5-96e5-c6bfabe4f9c2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6afa39993cf90b2d71b6b681680c3b4e1fd9b56b
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59826355"
---
# <a name="bitsadmin-peercaching-and-getconfigurationflags"></a>bitsadmin кэширования и getconfigurationflags



Получает флаги конфигурации, определяющие, если компьютер обслуживает содержимое для одноранговых узлов и можно загрузить содержимое из одноранговых узлов.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /PeerCaching /GetConfigurationFlags <Job> 
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|

## <a name="BKMK_examples"></a>Примеры

В следующем примере извлекается конфигурация флаги для задания с именем *myJob*.
```
C:\> Bitsadmin /PeerCaching /GetConfigurationFlags myJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)