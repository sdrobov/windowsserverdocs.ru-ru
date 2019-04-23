---
title: атрибуты тома
description: Раздел Windows команды для **атрибуты тома** -отображает наборы и очищает атрибуты тома.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e40e8284-3d57-4de8-a46c-e4ade34a0d53
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 37af55ee2a041fbcf8068e0def72147732d3a687
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59846585"
---
# <a name="attributes-volume"></a>атрибуты тома

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает, задает или удаляет атрибуты тома.  
  
  
  
## <a name="syntax"></a>Синтаксис  
  
```  
attributes volume [{set | clear}] [{hidden | readonly | nodefaultdriveletter | shadowcopy}] [noerr]  
```  
  
## <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|-------|--------|  
|набора|Устанавливает заданный атрибут тома с фокусом.|  
|clear|Удаляет указанный атрибут тома с фокусом.|  
|только для чтения|Указывает, что том доступен для чтения\-только.|  
|Скрытые|Указывает, что том является скрытым.|  
|nodefaultdriveletter|Указывает, что том не получает букву диска по умолчанию.|  
|Теневое копирование|Указывает, что том как том теневых копий.|  
|успешного|для использования в сценариях. При обнаружении ошибки, DiskPart продолжает обрабатывать команды, как если бы ошибки не было. Без этого параметра по ошибке будет возобновлено DiskPart завершить работу с кодом ошибки.|  
  
## <a name="remarks"></a>Примечания  
  
-   Основной загрузочной записи \(MBR\) дисков, **скрытые**, **readonly**, и **nodefaultdriveletter** параметры применяются ко всем томам на диск.  
  
-   На базовые таблица разделов GUID \(gpt\) диски и на динамических дисков MBR и gpt, **скрытые**, **readonly**, и **nodefaultdriveletter** параметры применяются только к выбранному тому.  
  
-   Должен быть выбран том **атрибуты тома** для успешного выполнения команды. Используйте **выберите том** команду, чтобы выбрать том и перетянуть внимание к нему.  
  
## <a name="BKMK_examples"></a>Примеры  
Чтобы отобразить текущие атрибуты выбранного тома, введите следующую команду:  
  
```  
attributes volume  
```  
  
Чтобы задать выбранный том как скрытый и чтения\-, введите:  
  
```  
attributes volume set hidden readonly  
```  
  
Удаление скрытых и чтения\-только атрибуты для выбранного тома, введите:  
  
```  
attributes volume clear hidden readonly  
```  
  
#### <a name="additional-references"></a>Дополнительные ссылки  
[Ключ синтаксиса командной строки](command-line-syntax-key.md)  
  

  

