---
title: bitsadmin getclientcertificate
description: Раздел Windows команды для **bitsadmin getclientcertificate** -извлекает сертификат клиента из задания.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4fc8f408-085e-43a0-9fa8-3d798ef107b1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 113d733d1deb9fbb1c89231495cb7af668a444d5
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59869045"
---
# <a name="bitsadmin-getclientcertificate"></a>bitsadmin getclientcertificate



Извлекает сертификат клиента из задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetClientCertificate <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|

## <a name="BKMK_examples"></a>Примеры

В следующем примере извлекается сертификата клиента для задания с именем *myDownloadJob*.
```
C:\>bitsadmin / GetClientCertificate myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)