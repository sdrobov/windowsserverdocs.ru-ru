---
title: битсадмин util и жетиепрокси
description: Раздел команд Windows для битсадмин util и жетиепрокси, который получает сведения об использовании прокси-сервера для данной учетной записи службы.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6d50c7e3-f4eb-4ca5-9f0c-4ed396087db6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d0d2a8634f3b42d655632a280cb9b998111c800b
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848977"
---
# <a name="bitsadmin-util-and-getieproxy"></a>битсадмин util и жетиепрокси

> Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Возвращает сведения об использовании прокси-сервера для данной учетной записи службы.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /Util /GetIEProxy <Account> [/Conn <ConnectionName>]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------|--------|
|Учетная запись|Указывает учетную запись службы, параметры прокси которой необходимо получить. Возможные значения:<p>-LOCALSYSTEM<br />-NETWORKSERVICE<br />-LOCALSERVICE|
|ConnectionName|Необязательно используется с параметром **/conn** для указания используемого подключения к модему. Если параметр **/conn** не указан, служба BITS использует подключение по локальной сети. Укажите имя подключения к модему сразу после параметра **/conn** .|

## <a name="remarks"></a>Примечания

Этот параметр показывает значение для каждого использования прокси-сервера, а не только использование прокси-сервера, указанного для учетной записи службы. Дополнительные сведения о настройке использования прокси-сервера для учетных записей служб см. в разделе [битсадмин util and сетиепрокси](bitsadmin-util-and-setieproxy.md) Switch.

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере показано использование прокси-сервера для учетной записи сетевой службы.

```
C:\>bitsadmin /Util /GetIEProxy NETWORKSERVICE
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
