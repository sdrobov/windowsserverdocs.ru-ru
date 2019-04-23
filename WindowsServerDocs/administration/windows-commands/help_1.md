---
title: справка
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 29ec2da9d383985d62931ce1cee9bd4a83a0fb1d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59869595"
---
# <a name="help"></a>справка

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает список доступных команд или подробной справки по указанной команде.  
  
  
  
## <a name="syntax"></a>Синтаксис  
  
```  
help [<command>]  
```  
  
## <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|-------|--------|  
|<command>|Указывает команду для отображения подробной справки.|  
  
## <a name="remarks"></a>Примечания  
  
-   Если команда не указана, **помочь** отобразит все возможные команды.  
  
## <a name="BKMK_examples"></a>Примеры  
Чтобы вывести список всех команд, доступных в DiskPart, введите следующую команду:  
  
```  
help  
```  
  
Чтобы отобразить подробные справочные сведения об использовании **создать основной раздел** в DiskPart, введите команду:  
  
```  
help create partition primary  
```  
  
#### <a name="additional-references"></a>Дополнительные ссылки  
[Ключ синтаксиса командной строки](command-line-syntax-key.md)  
  

  

