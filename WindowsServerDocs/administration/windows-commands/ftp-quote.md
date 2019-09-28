---
title: Цитата FTP
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4500a1d3-c091-42c7-a909-f61df7f2e993 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 65660cf7311713295dae8a94c9174229f5ee44be
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71376080"
---
# <a name="ftp-quote"></a>FTP: кавычка

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отправляет точные аргументы на удаленный FTP-сервер. Возвращается один код ответа FTP.   
## <a name="syntax"></a>Синтаксис  
```  
quote <Argument>[ ]  
```  
### <a name="parameters"></a>Параметры  

| Параметр  |                    Описание                    |
|------------|---------------------------------------------------|
| <Argument> | Указывает аргумент для отправки на FTP-сервер. |

## <a name="remarks"></a>Примечания  
Команда **quote** идентична команде **Literal** .  
## <a name="BKMK_Examples"></a>Примеров  
Отправка команды **Quit** на удаленный FTP-сервер.  
```  
quote quit  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [FTP: literal_1](ftp-literal_1.md)  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
