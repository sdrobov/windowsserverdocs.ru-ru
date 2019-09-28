---
title: mklink
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0ce4df22-2dbc-48fc-9c16-b721ae85f857
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9d930cbf7acbfceab16f2fa619aaaac6e789c131
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71373643"
---
# <a name="mklink"></a>mklink
Создает символьную ссылку.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
mklink [[/d] | [/h] | [/j]] <Link> <Target>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/d|Создает символьную ссылку каталога. По умолчанию **Mklink** создает символьную ссылку на файл.|
|/h|Создает жесткую связь вместо символьной ссылки.|
|/j|Создает соединение с каталогом.|
|@no__t 0Link >|Указывает имя создаваемой символьной ссылки.|
|@no__t 0Target >|Указывает путь (относительный или абсолютный), на который ссылается Новая символьная ссылка.|
|/?|Отображение справки в командной строке.|

## <a name="BKMK_examples"></a>Примеров

В примере входящей показано создание и удаление символической ссылки с именем MyFolder и MyFile. file из корневого каталога в каталог \Users\User1\Documents и файла example. File, расположенного в каталоге:
```
mklink /d \MyFolder \Users\User1\Documents
mklink /h \MyFile.file \User1\Documents\example.file
rd \MyFolder
del \MyFile.file
```
## <a name="additional-references"></a>Дополнительная справка
-   [Новый элемент](https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-item?view=powershell-6)
-   [del](https://docs.microsoft.com/windows-server/administration/windows-commands/del)
-   [rmdir](https://docs.microsoft.com/windows-server/administration/windows-commands/rd)
