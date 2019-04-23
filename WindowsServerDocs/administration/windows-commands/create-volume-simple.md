---
title: Создание простого тома
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: da0f208d-7fda-471a-9db2-5de5ba5207c6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d754a6b5788656132459a0b4a42954e9084f26bb
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59836505"
---
# <a name="create-volume-simple"></a>Создание простого тома

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Создание простого тома на динамическом диске.  
  
> [!IMPORTANT]  
> для Windows Vista эта команда DiskPart доступна только в выпусках Windows Vista Ultimate, Windows Vista Enterprise и Windows Vista Business.  
  
  
  
## <a name="syntax"></a>Синтаксис  
  
```  
create volume simple [size=<n>] [disk=<n>] [align=<n>] [noerr]  
```  
  
## <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|-------|--------|  
|Размер\=<n>|Размер тома в мегабайтах \(МБ\). Если размер не задан, новый том занимает свободное место на диске.|  
|диск\=<n>|Динамический диск, на котором создается том. Если диск не указан, используется текущий диск.|  
|Выравнивание\=<n>|Выравнивает все области тома до ближайшей границы выравнивания. Обычно используется с оборудованием логический номер устройства RAID \(LUN\) массивы для повышения производительности. *n* число килобайт \(КБ\) с самого начала диска до ближайшей границы выравнивания.|  
|успешного|для использования в сценариях. При обнаружении ошибки, DiskPart продолжает обрабатывать команды, как если бы ошибки не было. Без этого параметра по ошибке будет возобновлено DiskPart завершить работу с кодом ошибки.|  
  
## <a name="remarks"></a>Примечания  
  
-   После создания тома фокус автоматически переносится на новый том.  
  
## <a name="BKMK_examples"></a>Примеры  
Чтобы создать том с 1000 МБ размер на диске 1, введите:  
  
```  
create volume simple size=1000 disk=1  
```  
  
#### <a name="additional-references"></a>Дополнительные ссылки  
[Ключ синтаксиса командной строки](command-line-syntax-key.md)  
  

  

