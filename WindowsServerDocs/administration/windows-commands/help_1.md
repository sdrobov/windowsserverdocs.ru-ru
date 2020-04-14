---
title: help
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 75dbf94f-d79c-45b2-9463-c06648218f4a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 404cefe879e8f63678f2cba90516fad9c216eb23
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80842317"
---
# <a name="help"></a>help

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

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
  
## <a name="examples"></a><a name=BKMK_examples></a>Примеров  
Чтобы отобразить список всех команд, доступных в DiskPart, введите:  
  
```  
help  
```  
  
Чтобы просмотреть подробные справочные сведения о том, как использовать команду **создать секцию** в DiskPart, введите:  
  
```  
help create partition primary  
```  
  
## <a name="additional-references"></a>Дополнительные материалы  
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
  

  

