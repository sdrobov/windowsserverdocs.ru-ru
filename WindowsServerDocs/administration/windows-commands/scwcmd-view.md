---
title: Представление Scwcmd
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7995959a-d93e-4865-a6a0-2ab18c2bb47f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2ef1dd72903108edd6c5fb450c536a9325fcf546
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59889555"
---
# <a name="scwcmd-view"></a>Scwcmd: view

> Область применения. Windows Server 2012 R2, Windows Server 2012

Отображает XML-файл с помощью указанного .xsl преобразования. Эта команда может быть полезен для отображения мастера настройки безопасности (SCW) XML-файлов с помощью различных представлений.

## <a name="syntax"></a>Синтаксис

```
scwcmd view /x:<Xmlfile.xml> [/s:<Xslfile.xsl>]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/x:\<Xmlfile.xml>|Задает XML-файл для просмотра. Этот параметр должен быть указан.|
|/s:\<Xslfile.xsl>|Указывает .xsl преобразование для применения к XML-файла, в ходе процесса подготовки к просмотру. Этот параметр является необязательным для XML-файлов SCW. Когда **представление** команда используется для подготовки к просмотру в SCW XML-файл, он попытается автоматически загрузить правильный по умолчанию преобразование для указанного XML-файла. Если указано .xsl преобразование, преобразование должно быть написано таким образом, предполагается, что XML-файл находится в том же каталоге, что преобразование .xsl.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

Scwcmd.exe доступна только на компьютерах под управлением Windows Server 2008 R2, Windows Server 2008 или Windows Server 2003.

## <a name="BKMK_Examples"></a>Примеры

Чтобы просмотреть Policyfile.xml путем использования преобразования Policyview.xsl, введите следующую команду:
```
scwcmd view /x:C:\policies\Policyfile.xml /s:C:\viewers\Policyview.xsl
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)