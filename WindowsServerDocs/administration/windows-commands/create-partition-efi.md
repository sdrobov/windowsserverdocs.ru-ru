---
title: создать секцию EFI
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 76d97129fd67345f23eee2fc7b300493a1632cc6
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71379007"
---
# <a name="create-partition-efi"></a>создать секцию EFI

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

На компьютерах с процессорами Itanium @ no__t-0based создает расширяемый интерфейс микропрограмм \(EFI @ no__t-2 в таблице разделов GUID, \(gpt @ no__t-4.  
  
  
  
## <a name="syntax"></a>Синтаксис  
  
```  
create partition efi [size=<n>] [offset=<n>] [noerr]  
```  
  
## <a name="parameters"></a>Параметры  
  
|  Параметр  |                                                                                             Описание                                                                                              |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  size @ no__t-0 @ no__t-1  |                         Размер раздела в мегабайтах \(MB @ no__t-1. Если размер не указан, раздел будет продолжаться до тех пор, пока в текущем регионе не останется свободного места.                         |
| offset @ no__t-0 @ no__t-1 |             Смещение в килобайтах \(KB @ no__t-1, в котором создается секция. Если смещение не задано, раздел помещается в первый экстент диска, достаточно большой для его хранения.              |
|    Noerr    | только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки. |
  
## <a name="remarks"></a>Примечания  
  
-   После создания раздела фокус передается новой секции.  
  
-   Для выполнения этой операции необходимо выбрать диск GPT. Используйте команду **Выбор диска** , чтобы выбрать диск и переместить фокус на него.  
  
## <a name="BKMK_examples"></a>Примеров  
Чтобы создать раздел EFI с 1000 МБ на выбранном диске, введите:  
  
```  
create partition efi size=1000  
```  
  
#### <a name="additional-references"></a>Дополнительные ссылки  
[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
  

  

