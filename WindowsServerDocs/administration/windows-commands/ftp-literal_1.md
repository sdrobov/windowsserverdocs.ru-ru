---
title: literal_1 FTP
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: fb81aa2d-07fa-4e79-bf44-1fb5526fdf14 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f502bb56c94734870962f56cfb85dcc17ddc3f93
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843397"
---
# <a name="ftp-literal_1"></a>FTP: literal_1

>Область применения: Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, отправляет точные аргументы на удаленный FTP-сервер. Возвращается один код ответа FTP.   

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
## <a name="examples"></a><a name=BKMK_Examples></a>Примеров  
Отправка команды **Quit** на удаленный FTP-сервер.  
```  
literal quit  
```  
## <a name="additional-references"></a>Дополнительные материалы  
-   [FTP: кавычка](ftp-quote.md)  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
