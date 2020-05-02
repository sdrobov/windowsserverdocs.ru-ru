---
title: Цитата FTP
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4500a1d3-c091-42c7-a909-f61df7f2e993 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1101dd6a5fa163df8d43d182e9d0dfe66e340b60
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725143"
---
# <a name="ftp-quote"></a>FTP: кавычка

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

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
## <a name="examples"></a>Примеры  
Отправка команды **Quit** на удаленный FTP-сервер.  
```  
quote quit  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [FTP: literal_1](ftp-literal_1.md)  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
