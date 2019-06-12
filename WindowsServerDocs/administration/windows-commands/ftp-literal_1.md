---
title: FTP literal_1
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fb81aa2d-07fa-4e79-bf44-1fb5526fdf14 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 693916507488a9a480315a8e9299baa93a223b8a
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66438667"
---
# <a name="ftp-literal1"></a>ftp: literal_1

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 отправляет verbatim аргументы с удаленного FTP-сервером. Возвращается код ответа единый ftp.   

## <a name="syntax"></a>Синтаксис  
```  
literal <Argument> [ ]  
```  
### <a name="parameters"></a>Параметры  

| Параметр  |                    Описание                    |
|------------|---------------------------------------------------|
| <Argument> | Задает аргумент для отправки на сервер ftp. |

## <a name="remarks"></a>Примечания  
**Литерала** команда идентична **квоты** команды.  
## <a name="BKMK_Examples"></a>Примеры  
Отправить **выйти из программы** команду на удаленном FTP-сервер.  
```  
literal quit  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [FTP: Квота](ftp-quote.md)  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
