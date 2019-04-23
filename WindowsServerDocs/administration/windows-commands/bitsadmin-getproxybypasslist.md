---
title: bitsadmin getproxybypasslist
description: Раздел Windows команды для **bitsadmin getproxybypasslist** -извлекает список обхода прокси-сервера для указанного задания.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 50959be3-7014-4bc9-9a7b-68f1ff94a94a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 020b8fc0019eb103a0e469258be8705b80dd45de
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59854115"
---
# <a name="bitsadmin-getproxybypasslist"></a>bitsadmin getproxybypasslist

Извлекает список обхода прокси-сервера для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetProxyBypassList <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|

## <a name="remarks"></a>Примечания

В списке пропускаемых адресов содержит имена узлов или IP-адреса или оба параметра, они не будут направляться через прокси-сервер. Список может содержать "\<локальный >» для ссылки на все серверы в той же локальной сети. Список может быть точкой с запятой или с разделителями пробелами.

## <a name="BKMK_examples"></a>Примеры

В следующем примере извлекается список обхода прокси-сервера для задания с именем *myDownloadJob*.
```
C:\>bitsadmin /GetProxyBypassList myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)