---
title: Квота FTP
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 1f468bfc384673818dc53be303f82cd4803cb2eb
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66438491"
---
# <a name="ftp-quote"></a>FTP: Квота

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отправляет verbatim аргументы с удаленного FTP-сервером. Возвращается код ответа единый ftp.   
## <a name="syntax"></a>Синтаксис  
```  
quote <Argument>[ ]  
```  
### <a name="parameters"></a>Параметры  

| Параметр  |                    Описание                    |
|------------|---------------------------------------------------|
| <Argument> | Задает аргумент для отправки на сервер ftp. |

## <a name="remarks"></a>Примечания  
**Квоты** команда идентична **литерала** команды.  
## <a name="BKMK_Examples"></a>Примеры  
Отправить **выйти из программы** команду на удаленном FTP-сервер.  
```  
quote quit  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [ftp: literal_1](ftp-literal_1.md)  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
