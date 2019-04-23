---
title: sfc
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c58c25da-e028-42a6-9e10-973484a4b953
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1db0ab81c9469c88ddb64a367a9dc98a1fd9b70c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59832395"
---
# <a name="sfc"></a>sfc

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Сканирует и проверяет целостность все защищенные системные файлы и заменить ошибочные версии правильные версии.
Примеры для использования этой команды, см. в разделе [примеры](#BKMK_examples).

## <a name="syntax"></a>Синтаксис
```
sfc [/scannow] [/verifyonly] [/scanfile=<file>] [/verifyfile=<file>] [/offwindir=<offline windows directory> /offbootdir=<offline boot directory>]
```

### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/scannow|Проверяет целостность все защищенные системные файлы и восстанавливает файлы с проблемами, когда это возможно.|
|/ VERIFYONLY|Проверяет целостность все защищенные системные файлы. Операция восстановления не выполняется.|
|/scanfile|Проверяет целостность указанного файла и восстанавливает файл, если обнаружены проблемы, если это возможно.|
|\<Файл >|Указанный полный путь и имя файла|
|/verifyfile|проверяет целостность указанного файла. Операция восстановления не выполняется.|
|/offwindir|Указывает расположение каталога windows в автономном режиме, для автономного восстановления.|
|версий правильными|Указывает расположение каталога автономно загружаемая для автономный режим|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания
-   Необходимо войти в систему как член группы "Администраторы" для запуска **sfc.exe**.
-   Если **sfc** обнаруживает, что защищенный файл был изменен, он извлекает правильную версию файла, из **systemroot\system32\dllcache** папку, а затем заменяет неправильный файл.
-   Существуют функциональные различия между **sfc** на Windows Server 2003, Windows Server 2008 и Windows Server 2008 R2:
-   Дополнительные сведения о **sfc** на Windows Server 2003, см. в разделе [статьи 310747](https://go.microsoft.com/fwlink/?LinkId=227069) в базе знаний Майкрософт.
-   Дополнительные сведения о **sfc** на Windows Server 2008 и Windows Server 2008 R2, см. в разделе [системных файлов](https://go.microsoft.com/fwlink/?LinkId=227071).

## <a name="BKMK_examples"></a>Примеры
Чтобы проверить **файл kernel32.dll**, тип:
```
sfc /verifyfile=c:\windows\system32\kernel32.dll
```
Для установки автономного восстановления **kernel32.dll** файл с каталогом автономно загружаемая присвоено **d:** и автономный каталог windows присвоено **d:\windows**, тип:
```
sfc /scanfile=d:\windows\system32\kernel32.dll /offbootdir=d:\ /offwindir=d:\windows
```

## <a name="additional-references"></a>Дополнительная справка
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)

