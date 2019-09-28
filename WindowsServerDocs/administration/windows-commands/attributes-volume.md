---
title: Атрибуты тома
description: Раздел команд Windows для **атрибутов Volume** — отображение, установка или удаление атрибутов тома.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 225a10307123763d1a024fcc08fbae536fd0b5df
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71382580"
---
# <a name="attributes-volume"></a>Атрибуты тома

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает, устанавливает или очищает атрибуты тома.  
  
  
  
## <a name="syntax"></a>Синтаксис  
  
```  
attributes volume [{set | clear}] [{hidden | readonly | nodefaultdriveletter | shadowcopy}] [noerr]  
```  
  
## <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|-------|--------|  
|набора|Задает указанный атрибут тома с фокусом.|  
|clear|Очищает указанный атрибут тома с фокусом.|  
|Доступно|Указывает, что том доступен для чтения @ no__t-0only.|  
|служеб|Указывает, что том скрыт.|  
|нодефаултдривелеттер|Указывает, что том не получает букву диска по умолчанию.|  
|SHADOWCOPY|Указывает, что том является томом теневого копирования.|  
|Noerr|только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки.|  
  
## <a name="remarks"></a>Примечания  
  
-   На дисках с основной загрузочной записью \(MBR @ no__t-1 параметры **Hidden**, **ReadOnly**и **нодефаултдривелеттер** применяются ко всем томам на диске.  
  
-   В основной таблице разделов GUID \(gpt @ no__t-1, а также на динамических дисках MBR и GPT параметры **Hidden**, **ReadOnly**и **нодефаултдривелеттер** применяются только к выбранному тому.  
  
-   Чтобы команда **атрибутов тома** была выполнена, необходимо выбрать том. Используйте команду **выбрать том** , чтобы выбрать том и переместить фокус на него.  
  
## <a name="BKMK_examples"></a>Примеров  
Чтобы отобразить текущие атрибуты выбранного тома, введите:  
  
```  
attributes volume  
```  
  
Чтобы установить выбранный том как скрытый и прочитать @ no__t-0only, введите:  
  
```  
attributes volume set hidden readonly  
```  
  
Чтобы удалить скрытые и прочитанные атрибуты @ no__t-0only на выбранном томе, введите:  
  
```  
attributes volume clear hidden readonly  
```  
  
#### <a name="additional-references"></a>Дополнительные ссылки  
[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
  

  

