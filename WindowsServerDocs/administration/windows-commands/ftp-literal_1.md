---
title: literal_1 FTP
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 393dea27e8567a72a5bd25c927282ade93e317c9
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71376275"
---
# <a name="ftp-literal_1"></a>FTP: literal_1

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, отправляет на удаленный FTP-сервер точные аргументы. Возвращается один код ответа FTP.   

## <a name="syntax"></a>Синтаксис  
```  
literal <Argument> [ ]  
```  
### <a name="parameters"></a>Параметры  

| Параметр  |                    Описание                    |
|------------|---------------------------------------------------|
| <Argument> | Указывает аргумент для отправки на FTP-сервер. |

## <a name="remarks"></a>Примечания  
**Литеральная** команда идентична команде **quote** .  
## <a name="BKMK_Examples"></a>Примеров  
Отправка команды **Quit** на удаленный FTP-сервер.  
```  
literal quit  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [FTP: кавычка](ftp-quote.md)  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
