---
title: битсадмин жетпроксилист — извлекает список прокси-серверов для указанного задания.
description: Раздел команд Windows для **битсадмин жетпроксилист** — извлекает список прокси-серверов для указанного задания.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 6f176d268c816725b183da0a948afcb25272b2fb
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381310"
---
# <a name="bitsadmin-getproxylist"></a>bitsadmin getproxylist

Извлекает список прокси-серверов для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetProxyList <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="remarks"></a>Примечания

Список прокси-серверов — это список прокси-сервера для использования. Список разделен разделителями-запятыми.

## <a name="BKMK_examples"></a>Примеров

В следующем примере извлекается список прокси-серверов для задания с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /GetProxyList myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)