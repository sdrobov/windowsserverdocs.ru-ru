---
title: bitsadmin complete
description: Раздел Windows команды для **bitsadmin полный** -завершает задание. Загруженные файлы недоступны для вас, пока этот параметр используется.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a5e86677-8f7b-43b3-929e-97706c57e7f1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 561585da370f7e69aa3b83b3ddd7579bfc658a21
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59817325"
---
# <a name="bitsadmin-complete"></a>bitsadmin complete

Завершает задание. Загруженные файлы недоступны для вас, пока этот параметр используется. Этот параметр следует используйте после задание переходит в состояние переносятся. В противном случае доступны только те файлы, которые были успешно перенесены.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /complete <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|

## <a name="BKMK_examples"></a>Примеры

При ПЕРЕДАЧЕ состояние задания BITS успешно передаст все файлы в задание. Тем не менее, файлы не будут доступны только при вызове **/ завершения** переключения. Если использовать несколько заданий *myDownloadJob* в имени, необходимо заменить *myDownloadJob* с идентификатором GUID задания для уникальной идентификации задания.
```
C:\>bitsadmin /complete myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)