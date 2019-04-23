---
title: bitsadmin getproxylist - извлекает список прокси-сервера для указанного задания.
description: Раздел Windows команды для **bitsadmin getproxylist** -извлекает список прокси-сервера для указанного задания.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: eebfa727-d8f1-4ae3-9382-6d8ffe8c3df3
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e8c3ffb1e425552cda5b14a00287817ace77a90f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59840515"
---
# <a name="bitsadmin-getproxylist"></a>bitsadmin getproxylist

Извлекает список прокси-сервера для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetProxyList <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|

## <a name="remarks"></a>Примечания

Список прокси-сервера является список прокси-серверов для использования. Список с разделителями запятыми.

## <a name="BKMK_examples"></a>Примеры

В следующем примере извлекается список прокси-сервера для задания с именем *myDownloadJob*.
```
C:\>bitsadmin /GetProxyList myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)