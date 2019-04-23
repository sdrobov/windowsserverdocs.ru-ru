---
title: Создание раздела efi
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3cfc1fca-6515-4a4d-bfae-615fa8045ea9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3714cfe52aafd4a602346139552b6712dbbc98c1
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59878225"
---
# <a name="create-partition-efi"></a>Создание раздела efi

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

На базе процессоров Itanium\-компьютерах, создает Extensible Firmware Interface \(EFI\) системный раздел на таблица разделов GUID \(gpt\) диска.  
  
  
  
## <a name="syntax"></a>Синтаксис  
  
```  
create partition efi [size=<n>] [offset=<n>] [noerr]  
```  
  
## <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|-------|--------|  
|Размер\=<n>|Размер раздела в мегабайтах \(МБ\). Если размер не указан, раздел занимает имеется свободное пространство в текущей области.|  
|Смещение\=<n>|Смещение в килобайтах \(КБ\), в которой создается секция. Если смещение не указано, раздел помещается в первое пространство на диске, достаточное для их хранения.|  
|успешного|для использования в сценариях. При обнаружении ошибки, DiskPart продолжает обрабатывать команды, как если бы ошибки не было. Без этого параметра по ошибке будет возобновлено DiskPart завершить работу с кодом ошибки.|  
  
## <a name="remarks"></a>Примечания  
  
-   После создания секции, фокус перемещается на этот раздел.  
  
-   Gpt-диск должен быть выбран для выполнения данной операции. Используйте **выберите диск** команду, чтобы выбрать диск и перетянуть внимание к нему.  
  
## <a name="BKMK_examples"></a>Примеры  
Чтобы создать раздел EFI, 1000 МБ на диске, введите следующую команду:  
  
```  
create partition efi size=1000  
```  
  
#### <a name="additional-references"></a>Дополнительные ссылки  
[Ключ синтаксиса командной строки](command-line-syntax-key.md)  
  

  

