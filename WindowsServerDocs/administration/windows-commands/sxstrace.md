---
title: sxstrace
description: Узнайте, как диагностировать проблемы, связанные с параллельным выполнением.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 66326943bf1b056951ae5824df5a4f60892492cb
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71370708"
---
# <a name="sxstrace"></a>sxstrace

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Диагностика проблем с параллельным управлением.    

## <a name="syntax"></a>Синтаксис  
```  
sxstrace [{[trace -logfile:<FileName> [-nostop]|[parse -logfile:<FileName> -outfile:<ParsedFile>  [-filter:<AppName>]}]  
```  

### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|трассировка|Включает трассировку для SxS (параллельно)|  
|-файл_журнала|Указывает необработанный файл журнала.|  
|\<Имя файла >|Сохраняет журнал трассировки в файле *filename*.|  
|-не останавливаться|Указывает отсутствие запроса на прекращение трассировки.|  
|Проанализировать|Преобразует необработанный файл трассировки.|  
|-файл|Указывает имя выходного файла.|  
|\<Парседфиле >|Указывает имя файла проанализированного файла.|  
|-Filter|Позволяет фильтровать выходные данные.|  
|\<AppName >|Указывает имя приложения.|  
|стоптраце|Остановите трассировку, если она не была остановлена ранее.|  
|-?|Отображение справки в командной строке.|  

## <a name="BKMK_Examples"></a>Примеров  
Включите трассировку и сохраните файл трассировки в **сксстраце. ETL**:  
```  
sxstrace trace -logfile:sxstrace.etl  
```  
Перевод необработанного файла трассировки в удобочитаемый формат и сохранение результата в файле **сксстраце. txt**:  
```  
sxstrace parse -logfile:sxstrace.etl -outfile:sxstrace.txt  
```  

## <a name="additional-references"></a>Дополнительная справка  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
  
