---
title: bitsadmin setdisplayname
description: Раздел Windows команды для **bitsadmin setdisplayname** -задает отображаемое имя указанного задания.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 13706c53-fb5f-4879-b5ca-82531361d6e1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d50cd2785e42b554cee340abc97fe4e4b53adcfc
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59843675"
---
# <a name="bitsadmin-setdisplayname"></a>bitsadmin setdisplayname



Задает отображаемое имя указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetDisplayName <Job> <DisplayName>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|
|DisplayName|Текст, используемый для отображаемого имени указанного задания.|

## <a name="BKMK_examples"></a>Примеры

Следующий пример задает отображаемое имя для задания с именем *myDownloadJob* для *myDownloadJob2*.
```
C:\>bitsadmin /SetDisplayName myDownloadJob "Download Music Job"
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)