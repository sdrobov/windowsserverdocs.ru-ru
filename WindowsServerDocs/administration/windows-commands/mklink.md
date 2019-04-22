---
title: mklink
description: 'Раздел Windows команды для ***- '
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
ms.openlocfilehash: eabbf159a64ab5df7f45ece390d0c2fdb9956b80
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59826335"
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

Чтобы создать символьную ссылку с именем MyDocs из корневого каталога в каталог \Users\User1\Documents, введите следующую команду:
```
mklink /d \MyDocs \Users\User1\Documents
```
## <a name="additional-references"></a>Дополнительная справка
-   [Новый элемент](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.management/new-item?view=powershell-6)
