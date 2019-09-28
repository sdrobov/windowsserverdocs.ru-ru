---
title: кэш битсадмин и сетекспиратионтиме
description: Раздел команд Windows для **кэша битсадмин и сетекспиратионтиме** — задает время истечения срока действия кэша.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 00ea6e4e-b707-4b31-88dd-b61a78565c8d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 386c6659e4410b41669ade39d8af97829d81a1cb
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381920"
---
>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

# <a name="bitsadmin-cache-and-setexpirationtime"></a>кэш битсадмин и сетекспиратионтиме
Задает срок действия кэша.
## <a name="syntax"></a>Синтаксис
```
bitsadmin /Cache /SetExpirationtime secs
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|сек|Количество секунд до истечения срока действия кэша.|
## <a name="BKMK_examples"></a>Примеров
В следующем примере срок действия кэша истекает через 60 секунд.
```
C:\>bitsadmin /Cache / SetExpirationtime 60
```
## <a name="additional-references"></a>Дополнительные ссылки
[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
