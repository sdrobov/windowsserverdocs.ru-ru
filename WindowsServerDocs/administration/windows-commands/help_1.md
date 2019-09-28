---
title: справка
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 75dbf94f-d79c-45b2-9463-c06648218f4a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c3d76a71ec287e5c874ae3e4dec34016c5c80336
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71375577"
---
# <a name="help"></a>справка

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает список доступных команд или подробные справочные сведения об указанной команде.  
  
  
  
## <a name="syntax"></a>Синтаксис  
  
```  
help [<command>]  
```  
  
## <a name="parameters"></a>Параметры  
  
| Параметр |                              Описание                              |
|-----------|-----------------------------------------------------------------------|
| <command> | Указывает команду, для которой отображаются подробные справочные сведения. |
  
## <a name="remarks"></a>Примечания  
  
-   Если команда не указана, в **справке** будут отображаться все возможные команды.  
  
## <a name="BKMK_examples"></a>Примеров  
Чтобы отобразить список всех команд, доступных в DiskPart, введите:  
  
```  
help  
```  
  
Чтобы просмотреть подробные справочные сведения о том, как использовать команду **создать секцию** в DiskPart, введите:  
  
```  
help create partition primary  
```  
  
#### <a name="additional-references"></a>Дополнительные ссылки  
[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
  

  

