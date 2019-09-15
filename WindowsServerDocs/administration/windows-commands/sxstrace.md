---
title: sxstrace
description: Узнайте, как диагностировать проблемы, связанные с параллельным выполнением.
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
ms.openlocfilehash: dbc8dad642e15dede1ce89105a501fd90224610b
ms.sourcegitcommit: feec5cbe983c8c5800ccd4fc214914084fcceaba
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2019
ms.locfileid: "70975310"
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

## <a name="additional-references"></a>Дополнительные ссылки  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
  
