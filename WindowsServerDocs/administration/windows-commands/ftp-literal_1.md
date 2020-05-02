---
title: literal_1 FTP
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: fb81aa2d-07fa-4e79-bf44-1fb5526fdf14 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fc4f8aff5a22da93330a12a75e5f368285366216
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725250"
---
# <a name="ftp-literal_1"></a>FTP: literal_1

> Область применения: Windows Server (полугодовой канал), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 отправляет на удаленный FTP-сервер точные аргументы. Возвращается один код ответа FTP.   

## <a name="syntax"></a>Синтаксис  
```  
literal <Argument> [ ]  
```  
#### <a name="parameters"></a>Параметры  

| Параметр  |                    Описание                    |
|------------|---------------------------------------------------|
| <Argument> | Указывает аргумент для отправки на FTP-сервер. |

## <a name="remarks"></a>Примечания  
**Литеральная** команда идентична команде **quote** .  
## <a name="examples"></a>Примеры  
Отправка команды **Quit** на удаленный FTP-сервер.  
```  
literal quit  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [FTP: кавычка](ftp-quote.md)  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
