---
title: 'Secedit: Проверка'
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9fb06354-f55a-4ca4-9fbc-9a872eb9b9cf
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ece0a0324b77eb4226b679bc29f7bd599f15a120
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71371105"
---
# <a name="seceditvalidate"></a>Secedit: Проверка



Проверяет параметры безопасности, хранящиеся в шаблоне безопасности (INF-файле). Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
Secedit /validate <configuration file name>  

```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Имя файла конфигурации|Обязательный.</br>Указывает путь и имя файла для шаблона безопасности, который будет проверен.|

## <a name="remarks"></a>Примечания

Проверка шаблонов безопасности может помочь в том, что один из них поврежден или настроен неправильно.

Недопустимый шаблон безопасности не будет применен.

Файл журнала не будет обновлен.

В Windows Server 2008 `Secedit /refreshpolicy` был заменен на. `gpupdate` Сведения о том, как обновить параметры безопасности, см. в разделе [gpupdate](gpupdate.md).

## <a name="BKMK_Examples"></a>Примеров

После выполнения отката в шаблоне безопасности необходимо убедиться, что INF-файл отката Секрбкконтосо. inf является допустимым.
```
Secedit /validate secRBKcontoso.inf
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Secedit:generaterollback](secedit-generaterollback.md)
-   [Программу Secedit](secedit.md)
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)