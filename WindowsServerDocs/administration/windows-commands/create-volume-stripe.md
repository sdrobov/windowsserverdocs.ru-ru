---
title: Создание чередующегося тома
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 20dce735-5f7c-4f83-a580-d087e2913a00
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 197864c6908645af0c0fa47ac811186207c2f247
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59853885"
---
# <a name="create-volume-stripe"></a>Создание чередующегося тома

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Создание чередующегося тома с помощью двух или более указанных динамических дисков.  
  
> [!IMPORTANT]  
> для Windows Vista эта команда DiskPart доступна только в выпусках Windows Vista Ultimate, Windows Vista Enterprise и Windows Vista Business.  
  
  
  
## <a name="syntax"></a>Синтаксис  
  
```  
create volume stripe [size=<n>] disk=<n>,<n>[,<n>,...] [align=<n>] [noerr]  
```  
  
## <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|-------|--------|  
|Размер\=<n>|Объем места на диске в мегабайтах \(МБ\), том будет занимать на каждом диске. Если размер не задан, новый том занимает самый маленький диск и равное количество места на каждом последующем диске свободное место.|  
|диск\=<n>,<n>\[,<n>,...\]|Динамические диски, на которых создается чередующийся том. Необходимо по крайней мере два динамических дисков для создания чередующегося тома. Объем пространства, равным **размер\= <n>**  выделяется на каждом диске.|  
|Выравнивание\=<n>|Выравнивает все области тома до ближайшей границы выравнивания. Обычно используется с оборудованием логический номер устройства RAID \(LUN\) массивы для повышения производительности. *n* число килобайт \(КБ\) с самого начала диска до ближайшей границы выравнивания.|  
|успешного|для использования в сценариях. При обнаружении ошибки, DiskPart продолжает обрабатывать команды, как если бы ошибки не было. Без этого параметра по ошибке будет возобновлено DiskPart завершить работу с кодом ошибки.|  
  
## <a name="remarks"></a>Примечания  
  
-   После создания тома фокус автоматически переносится на новый том.  
  
## <a name="BKMK_examples"></a>Примеры  
Чтобы создать чередующийся том 1000 МБ размер на дисках, 1 и 2, введите:  
  
```  
create volume stripe size=1000 disk=1,2  
```  
  
#### <a name="additional-references"></a>Дополнительные ссылки  
[Ключ синтаксиса командной строки](command-line-syntax-key.md)  
  

  

