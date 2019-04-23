---
title: bitsadmin setpriority
description: Раздел Windows команды для **bitsadmin setpriority** -задает приоритет для указанного задания.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 90788363-01a2-4d7c-a560-a3eba45b5e9e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 072f22ae8c928d427104062b8cbf0f8f42ac4416
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59882215"
---
# <a name="bitsadmin-setpriority"></a>bitsadmin setpriority



Задает приоритет для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetPriority <Job> <Priority>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|
|Priority|Принимает одно из следующих значений:</br>-ПЕРЕДНЕГО ПЛАНА</br>-ВЫСОКИЙ</br>-НОРМ.</br>-LOW|

## <a name="BKMK_examples"></a>Примеры

В следующем примере задается приоритет задания с именем *myDownloadJob* в нормальное состояние.
```
C:\>bitsadmin /SetPriority myDownloadJob NORMAL
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)