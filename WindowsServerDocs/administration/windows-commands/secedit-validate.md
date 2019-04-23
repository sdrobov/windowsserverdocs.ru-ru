---
title: 'Secedit: проверка'
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: cca64f6b2904ed11f6b45e316c8e4da0093c373e
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59877915"
---
# <a name="seceditvalidate"></a>Secedit: проверка



Проверяет параметры безопасности, хранящиеся в шаблоне безопасности (INF-файл). Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
Secedit /validate <configuration file name>  

```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Имя файла конфигурации|Обязательный.</br>Указывает путь и имя файла шаблона безопасности, который будет проверяться.|

## <a name="remarks"></a>Примечания

Проверка шаблонов параметров безопасности может помочь, если один является поврежден или неправильно задано.

Шаблон недопустимый безопасности не применяются.

Файл журнала не будет обновляться.

В Windows Server 2008 `Secedit /refreshpolicy` был заменен `gpupdate`. Сведения о том, как обновить параметры безопасности, см. в разделе [Gpupdate](gpupdate.md).

## <a name="BKMK_Examples"></a>Примеры

После выполнения отката на шаблон безопасности, который вы хотите убедитесь, что откат INF-файла, secRBKcontoso.inf, является допустимым.
```
Secedit /validate secRBKcontoso.inf
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Secedit:generaterollback](secedit-generaterollback.md)
-   [Secedit](secedit.md)
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)