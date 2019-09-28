---
title: bitsadmin getproxyusage
description: Раздел команд Windows для **битсадмин жетпроксюсаже** — получение параметра использования прокси-сервера для указанного задания.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: ea9a22f4fb35af3436d02d9f23b62ce0888a26b0
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381288"
---
# <a name="bitsadmin-getproxyusage"></a>bitsadmin getproxyusage



Извлекает параметр использования прокси-сервера для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetProxyUsage <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="remarks"></a>Примечания

Возможные значения:
-   Преднастройка — используйте значения по умолчанию для свойства Owner в Internet Explorer.
-   NO_PROXY — не использовать прокси-сервер.
-   Переопределение — Используйте явный список прокси-серверов.
-   Автообнаружение — автоматическое определение параметров прокси-сервера.

## <a name="BKMK_examples"></a>Примеров

В следующем примере извлекается использование прокси-сервера для задания с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /GetProxyUsage myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)