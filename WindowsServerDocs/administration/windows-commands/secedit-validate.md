---
title: 'Secedit: Проверка'
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9fb06354-f55a-4ca4-9fbc-9a872eb9b9cf
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b9425f7a1fb821f4ecbaa7c1689c3baabbff6223
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80834877"
---
# <a name="seceditvalidate"></a>Secedit: Проверка



Проверяет параметры безопасности, хранящиеся в шаблоне безопасности (INF-файле). Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
Secedit /validate <configuration file name>  

```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Имя файла конфигурации|Обязательное.</br>Указывает путь и имя файла для шаблона безопасности, который будет проверен.|

## <a name="remarks"></a>Примечания

Проверка шаблонов безопасности может помочь в том, что один из них поврежден или настроен неправильно.

Недопустимый шаблон безопасности не будет применен.

Файл журнала не будет обновлен.

В Windows Server 2008 `Secedit /refreshpolicy` был заменен `gpupdate`. Сведения о том, как обновить параметры безопасности, см. в разделе [gpupdate](gpupdate.md).

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров

После выполнения отката в шаблоне безопасности необходимо убедиться, что INF-файл отката Секрбкконтосо. inf является допустимым.
```
Secedit /validate secRBKcontoso.inf
```

## <a name="additional-references"></a>Дополнительные материалы

-   [Secedit:generaterollback](secedit-generaterollback.md)
-   [Программу Secedit](secedit.md)
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)