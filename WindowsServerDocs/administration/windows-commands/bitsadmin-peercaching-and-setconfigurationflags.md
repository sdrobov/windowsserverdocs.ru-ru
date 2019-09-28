---
title: битсадмин (кэшированный) и сетконфигуратионфлагс
description: Раздел команд Windows для **битсадмин и сетконфигуратионфлагс** . задает флаги конфигурации, которые определяют, может ли компьютер передавать содержимое одноранговым узлам, а также скачивать содержимое с одноранговых узлов.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: a65d54bcaa2bce26eb2b7c98250837ab09c7a423
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381113"
---
# <a name="bitsadmin-peercaching-and-setconfigurationflags"></a>битсадмин (кэшированный) и сетконфигуратионфлагс



Задает флаги конфигурации, которые определяют, может ли компьютер передавать содержимое одноранговым узлам, а также скачивать содержимое с одноранговых узлов.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /PeerCaching /SetConfigurationFlags <Job> <Value>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|
|Значение|Значение представляет собой целое число без знака со следующей интерпретацией битов в двоичном представлении:</br>— Разрешить загрузку данных задания с однорангового узла: Задать наименьший значащий бит</br>— Разрешить предоставлять данные задания одноранговым узлам: Установите 2-й бит справа.|

## <a name="BKMK_examples"></a>Примеров

В следующем примере указываются данные задания, которые должны быть загружены с одноранговых узлов для задания с именем *myJob*.
```
C:\> Bitsadmin /PeerCaching /SetConfigurationFlags myJob 1
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)