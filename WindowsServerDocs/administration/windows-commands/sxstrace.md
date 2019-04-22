---
title: sxstrace
description: Узнайте, как для диагностики проблем side-by-side.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fcd26eeb-fbd9-4a86-b6a9-dfa5e9c6e4fc
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 396d06bf079c0cfa8ba4864f71333eec39f7b255
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59814105"
---
# <a name="sxstrace"></a>sxstrace

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Диагностика проблем side-by-side.    

## <a name="syntax"></a>Синтаксис  
```  
sxstrace [{[trace /logfile:<FileName> [/nostop]|[parse /logfile:<FileName> /outfile:<ParsedFile>  [/filter:<AppName>]}]  
```  

### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|трассировка|Включает трассировку для sxs (side-by-side)|  
|/ LogFile|Указывает файл необработанных журналов.|  
|\<Имя файла >|Сохраняет журнал трассировки для *FileName*.|  
|/nostop|Указывает без запроса, чтобы остановить трассировку.|  
|Синтаксический анализ|Преобразует исходный файл трассировки.|  
|/ outfile|Указывает имя выходного файла.|  
|\<ParsedFile>|Указывает имя файла проанализированный файл.|  
|/ filter может|Позволяет осуществлять фильтрацию вывода.|  
|\<Имя_приложения >|Задает имя приложения.|  
|stoptrace|Остановите трассировку, если она не была завершена до.|  
|/?|Отображение справки в командной строке.|  

## <a name="BKMK_Examples"></a>Примеры  
Включение трассировки и сохранить файл трассировки для **sxstrace.etl**:  
```  
sxstrace trace /logfile:sxstrace.etl  
```  
Преобразует исходный файл трассировки в читаемом формате и сохранить результат **sxstrace.txt**:  
```  
sxstrace parse /logfile:sxstrace.etl /outfile:sxstrace.txt  
```  

## <a name="additional-references"></a>Дополнительная справка  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
  
