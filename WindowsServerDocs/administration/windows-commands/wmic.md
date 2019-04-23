---
title: wmic
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 76397c72-d06f-4cea-88cf-c7603315a983
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6c68866fbe0c8f5b16dae77e2121331f06cdc726
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59885845"
---
# <a name="wmic"></a>wmic



Отображает сведения о WMI в интерактивной среде.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
command </parameter>
```

## <a name="sub-commands"></a>Вложенные команды

Следующие вложенные команды доступны все время:

|Подкоманда|Описание|
|-----------|-----------|
|класс|Escape-последовательности по умолчанию псевдонима WMIC в прямой доступ к классам в схеме WMI.|
|path|Escape-последовательности по умолчанию псевдонима WMIC в прямой доступ к экземплярам в схеме WMI.|
|Контекст|Отображает текущие значения всех глобальных переключателей.|
|[выйти из программы \| выйти]|Выход из программы WMIC командную оболочку.|

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|</parameter>|\<Краткое описание начинается с команды. >|
|</param2>|\<Другой краткое описание, начинается с команды. >|


## <a name="BKMK_examples"></a>Примеры

Чтобы отобразить текущие значения всех глобальных параметров, введите следующую команду:
```
wmic context
```
Результат, аналогичный приведенному появится следующее:
```
NAMESPACE    : root\cimv2
ROLE         : root\cli
NODE(S)      : BOBENTERPRISE
IMPLEVEL     : IMPERSONATE
[AUTHORITY   : N/A]
AUTHLEVEL    : PKTPRIVACY
LOCALE       : ms_409
PRIVILEGES   : ENABLE
TRACE        : OFF
RECORD       : N/A
INTERACTIVE  : OFF
FAILFAST     : OFF
OUTPUT       : STDOUT
APPEND       : STDOUT
USER         : N/A
AGGREGATE    : ON
```
Чтобы изменить язык код используется командной строки на английском языке (языковой стандарт идентификатор 409), тип:
```
wmic /locale:ms_409
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)