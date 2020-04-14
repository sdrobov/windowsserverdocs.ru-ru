---
title: Цитата FTP
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4500a1d3-c091-42c7-a909-f61df7f2e993 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1bf13704150d602fbfa4e3b1a3fb1774d3bf7363
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843037"
---
# <a name="ftp-quote"></a>FTP: кавычка

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отправляет точные аргументы на удаленный FTP-сервер. Возвращается один код ответа FTP.   
## <a name="syntax"></a>Синтаксис  
```  
quote <Argument>[ ]  
```  
#### <a name="parameters"></a>Параметры  

| Параметр  |                    Описание                    |
|------------|---------------------------------------------------|
| <Argument> | Указывает аргумент для отправки на FTP-сервер. |

## <a name="remarks"></a>Примечания  
Команда **quote** идентична команде **Literal** .  
## <a name="examples"></a><a name=BKMK_Examples></a>Примеров  
Отправка команды **Quit** на удаленный FTP-сервер.  
```  
quote quit  
```  
## <a name="additional-references"></a>Дополнительные материалы  
-   [FTP: literal_1](ftp-literal_1.md)  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
