---
title: bitsadmin getproxyusage
description: Раздел Windows команды для **bitsadmin getproxyusage** — получает параметр использования прокси-сервера для указанного задания.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f940a70e-3b02-497e-a47f-b37b905c299e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 20ba418b8dfcf3d96d9b20b22e53797a232a13f1
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59863885"
---
# <a name="bitsadmin-getproxyusage"></a>bitsadmin getproxyusage



Получает параметр использования прокси-сервера для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetProxyUsage <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|

## <a name="remarks"></a>Примечания

Возможными значениями являются:
-   НАСТРОЕННОГО — использовать значения по умолчанию Internet Explorer владельца.
-   NO_PROXY — не использовать прокси-сервер.
-   ПЕРЕОПРЕДЕЛИТЬ — использовать список явных прокси-сервера.
-   АВТООБНАРУЖЕНИЕ — автоматическое определение параметров прокси-сервера.

## <a name="BKMK_examples"></a>Примеры

В следующем примере извлекается использование прокси-сервера для задания с именем *myDownloadJob*.
```
C:\>bitsadmin /GetProxyUsage myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)