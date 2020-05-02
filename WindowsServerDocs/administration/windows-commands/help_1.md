---
title: справка
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 75dbf94f-d79c-45b2-9463-c06648218f4a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6887edfd41895bb151c5aaebb88d8b72198f4dbf
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724901"
---
# <a name="help"></a>справка

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает список доступных команд или подробные справочные сведения об указанной команде.  
  
  
  
## <a name="syntax"></a>Синтаксис  
  
```  
help [<command>]  
```  
  
### <a name="parameters"></a>Параметры  
  
| Параметр |                              Описание                              |
|-----------|-----------------------------------------------------------------------|
| <command> | Указывает команду, для которой отображаются подробные справочные сведения. |
  
## <a name="remarks"></a>Примечания  
  
-   Если команда не указана, в **справке** будут отображаться все возможные команды.  
  
## <a name="examples"></a>Примеры  
Чтобы отобразить список всех команд, доступных в DiskPart, введите:  
  
```  
help  
```  
  
Чтобы просмотреть подробные справочные сведения о том, как использовать команду **создать секцию** в DiskPart, введите:  
  
```  
help create partition primary  
```  
  
## <a name="additional-references"></a>Дополнительные ссылки  
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
  

  

