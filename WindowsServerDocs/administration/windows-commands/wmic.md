---
title: wmic
description: Справочный раздел по WMIC, который отображает сведения WMI в интерактивной командной оболочке.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 76397c72-d06f-4cea-88cf-c7603315a983
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 252ba6b59c29378dd1f5e437de21a2ec4f5ec5c8
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720646"
---
# <a name="wmic"></a>wmic



Отображает сведения WMI в интерактивной командной оболочке.



## <a name="syntax"></a>Синтаксис

```
wmic </parameter>
```

## <a name="sub-commands"></a>Подкоманды

Следующие подкоманды доступны в любое время:

|Подкоманда|Описание|
|-----------|-----------|
|class|Отменяет режим псевдонима по умолчанию WMIC для прямого доступа к классам в схеме WMI.|
|path|Отменяет режим псевдонима по умолчанию WMIC для доступа к экземплярам в схеме WMI напрямую.|
|контекст|Отображает текущие значения всех глобальных коммутаторов.|
|[выход \| из программы]|Выход из командной оболочки WMIC.|

## <a name="examples"></a>Примеры

Чтобы отобразить текущие значения всех глобальных коммутаторов, введите:
```
wmic context
```
Выходные данные, аналогичные приведенным ниже, отображаются:
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
Чтобы изменить идентификатор языка, используемый в командной строке, на английский (код локали 409), введите:
```
wmic /locale:ms_409
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
