---
title: bitsadmin кэширования и setconfigurationflags
description: Раздел Windows команды для **bitsadmin кэширования и setconfigurationflags** -задает конфигурации флаги, определяющие, если компьютер может обслуживать содержимое для одноранговых узлов и можно загрузить содержимое из одноранговых узлов.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ff0a2b49-66e3-4d40-824c-6a3816055d2e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 22408d4aab7f5ea374511bc16751d911a84644f2
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59813335"
---
# <a name="bitsadmin-peercaching-and-setconfigurationflags"></a>bitsadmin кэширования и setconfigurationflags



Задает флаги конфигурации, определяющие, если компьютер может обслуживать содержимое для одноранговых узлов и можно загрузить содержимое из одноранговых узлов.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /PeerCaching /SetConfigurationFlags <Job> <Value>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|
|Значение|Значение — целое число без знака с следующую интерпретацию битам в двоичное представление:</br>-Разрешите загрузку из однорангового узла данных задания: Задать младший значащий бит</br>— Разрешите данных задания обслуживаются узлам: Установите 2-й бит справа.|

## <a name="BKMK_examples"></a>Примеры

В следующем примере задается загрузку от одноранговых узлов для задания данных задания *myJob*.
```
C:\> Bitsadmin /PeerCaching /SetConfigurationFlags myJob 1
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)