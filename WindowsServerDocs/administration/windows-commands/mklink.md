---
title: mklink
description: 'Раздел команд Windows для * * * *- '
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
ms.openlocfilehash: b7a5f9b819f16d058feb1dee74a8408ed174e04c
ms.sourcegitcommit: b7f55949f166554614f581c9ddcef5a82fa00625
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72588041"
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
|\<Link >|Указывает имя создаваемой символьной ссылки.|
|\<Target >|Указывает путь (относительный или абсолютный), на который ссылается Новая символьная ссылка.|
|/?|Отображение справки в командной строке.|

## <a name="BKMK_examples"></a>Примеров

В следующем примере демонстрируется создание и удаление символьной ссылки с именем MyFolder и MyFile. file из корневого каталога в каталог \Users\User1\Documents и файл example. File, находящийся в каталоге:
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
