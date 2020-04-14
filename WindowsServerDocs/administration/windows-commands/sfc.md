---
title: sfc
description: Раздел команд Windows для SFC, который сканирует и проверяет целостность всех защищенных системных файлов и заменяет неверные версии на правильные версии.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c58c25da-e028-42a6-9e10-973484a4b953
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7663c8e3527995e2d3ec874dff6fa972e7e83ddd
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80834327"
---
# <a name="sfc"></a>sfc

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Проверяет целостность всех защищенных системных файлов и заменяет их правильными версиями.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис
```
sfc [/scannow] [/verifyonly] [/scanfile=<file>] [/verifyfile=<file>] [/offwindir=<offline windows directory> /offbootdir=<offline boot directory>]
```

#### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/scannow|Проверяет целостность всех защищенных системных файлов и восстанавливает файлы с проблемами, когда это возможно.|
|/верифйонли|Проверяет целостность всех защищенных системных файлов. Операции восстановления не выполняются.|
|/сканфиле|Проверяет целостность указанного файла и восстанавливает файл, если это возможно.|
|\<файл >|Указанный полный путь и имя файла|
|/верифифиле|проверяет целостность указанного файла. Операции восстановления не выполняются.|
|/оффвиндир|Указывает расположение автономного каталога Windows для восстановления в автономном режиме.|
|/оффбутдир|Указывает расположение автономного каталога загрузки для автономной работы|
|/?|Отображает справку в командной строке.|

## <a name="remarks"></a>Примечания
-   Для запуска **sfc. exe**необходимо войти в систему в качестве члена группы "Администраторы".
-   Если **sfc** обнаруживает, что защищенный файл был перезаписан, он извлекает правильную версию файла из папки **systemroot\system32\dllcache** , а затем заменяет неверный файл.
-   Между **sfc** в windows Server 2003, windows Server 2008 и windows Server 2008 R2 существуют функциональные различия:
-   Дополнительные сведения о **sfc** в Windows Server 2003 см. в [статье 310747](https://go.microsoft.com/fwlink/?LinkId=227069) в базе знаний Майкрософт.
-   Дополнительные сведения о **sfc** в windows Server 2008 и windows Server 2008 R2 см. в разделе [средство проверки системных файлов](https://go.microsoft.com/fwlink/?LinkId=227071).

## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы проверить **файл Kernel32. dll**, введите:
```
sfc /verifyfile=c:\windows\system32\kernel32.dll
```
Чтобы настроить автономное восстановление файла **kernel32. dll** с автономной загрузочной папкой **d:** и автономным каталогом Windows, установленным в **d:\Windows**, введите:
```
sfc /scanfile=d:\windows\system32\kernel32.dll /offbootdir=d:\ /offwindir=d:\windows
```

## <a name="additional-references"></a>Дополнительная справка
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

