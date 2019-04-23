---
title: bitsadmin addfileset
description: Раздел Windows команды для **bitsadmin addfileset** -добавляет один или несколько файлов для указанного задания.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 75466994-262f-4724-b14d-f813c5397675
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f8f6ff32dfa6042272c68647477d77183ce9cb76
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59889445"
---
# <a name="bitsadmin-addfileset"></a>bitsadmin addfileset

Добавляет один или несколько файлов для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /addfileset <Job> <TextFile>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|
|Текстовый файл|Текстовый файл, каждая строка которого содержит удаленное и локальное имя файла.</br>Примечание. Имена, разделенные пробелами. Строки, начинающиеся с символа #, рассматриваются как комментарий.|

## <a name="BKMK_examples"></a>Примеры

```
C:\>bitsadmin /addfileset files.txt
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)