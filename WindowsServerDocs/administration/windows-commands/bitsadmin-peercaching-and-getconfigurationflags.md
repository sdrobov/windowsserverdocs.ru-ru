---
title: битсадмин (кэшированный) и жетконфигуратионфлагс
description: Раздел команд Windows для **битсадмин кэширования и жетконфигуратионфлагс** — Получает флаги конфигурации, которые определяют, обслуживает ли компьютер содержимое одноранговым узлам, и могут скачивать содержимое с одноранговых узлов.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 94c7eb1a115fe9152b149b8cf65765b179080cc3
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381086"
---
# <a name="bitsadmin-peercaching-and-getconfigurationflags"></a>битсадмин (кэшированный) и жетконфигуратионфлагс



Возвращает флаги конфигурации, определяющие, будет ли компьютер обслуживать содержимое одноранговым узлам, а также скачивать содержимое с одноранговых узлов.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /PeerCaching /GetConfigurationFlags <Job> 
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="BKMK_examples"></a>Примеров

В следующем примере показано получение флагов конфигурации для задания с именем *myJob*.
```
C:\> Bitsadmin /PeerCaching /GetConfigurationFlags myJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)