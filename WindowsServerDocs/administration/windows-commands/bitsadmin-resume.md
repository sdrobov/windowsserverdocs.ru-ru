---
title: bitsadmin resume
description: Раздел Windows команды для **bitsadmin resume** -активирует нового или приостановленного задания в очереди передачи.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7c7540a9-a11a-4910-923a-2a2a61cbf11d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 76027ac927f8a9bb2558e3ce6d75e4f6692e56e7
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59842035"
---
# <a name="bitsadmin-resume"></a>bitsadmin resume



Активирует нового или приостановленного задания в очереди передачи.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /Resume <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|

## <a name="BKMK_examples"></a>Примеры

Следующий пример возобновляет задания с именем *myDownloadJob*.
```
C:\>bitsadmin /Resume myDownloadJob
```
Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)