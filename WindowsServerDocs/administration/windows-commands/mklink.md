---
title: mklink
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 1ea80b81b268b31f637c72a828fee8b6f0229a47
ms.sourcegitcommit: afb0602767de64a76aaf9ce6a60d2f0e78efb78b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/20/2019
ms.locfileid: "67280026"
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
|/d|Создание символической ссылки каталога. По умолчанию **mklink** создает Символическая ссылка на файл.|
|/h|Создает жесткую связь вместо символьную ссылку.|
|/j|Создание соединения для каталога.|
|\<Ссылка >|Задает имя используемого символьную ссылку, который создается.|
|\<Целевой объект >|Указывает путь (относительный или абсолютный), адресованный новую символическую связь.|
|/?|Отображение справки в командной строке.|

## <a name="BKMK_examples"></a>Примеры

В следующем примере демонстрируется создание и удаление связей с именем MyFolder и MyFile.file из корневого каталога в каталог \Users\User1\Documents и example.file, расположенный в каталоге:
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
