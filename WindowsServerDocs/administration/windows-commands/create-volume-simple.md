---
title: создать простой том
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 1afb97c5bdb167eaf6ecfcd34ca3607b7b5a4c71
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71378877"
---
# <a name="create-volume-simple"></a>создать простой том

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

создает простой том на указанном динамическом диске.  
  
> [!IMPORTANT]  
> для Windows Vista эта команда DiskPart доступна только в выпусках Windows Vista Ultimate, Windows Vista Корпоративная и Windows Vista Business.  
  
  
  
## <a name="syntax"></a>Синтаксис  
  
```  
create volume simple [size=<n>] [disk=<n>] [align=<n>] [noerr]  
```  
  
## <a name="parameters"></a>Параметры  
  
| Параметр  |                                                                                                                            Описание                                                                                                                            |
|------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| size @ no__t-0 @ no__t-1  |                                                                  Размер тома в мегабайтах \(MB @ no__t-1. Если размер не указан, новый том занимает оставшееся свободное пространство на диске.                                                                   |
| Disk @ no__t-0 @ no__t-1  |                                                                                Динамический диск, на котором создается том. Если диск не указан, используется текущий диск.                                                                                |
| ALIGNED @ no__t-0 @ no__t-1 | Выравнивает все экстенты томов по ближайшей границе выравнивания. Обычно используется с аппаратными массивами RAID с номерами устройств \(LUN @ no__t-1 для повышения производительности. *n* — это количество килобайтов \( КБ @ no__t-2 от начала диска до ближайшей границы выравнивания. |
|   Noerr    |                               только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки.                                |
  
## <a name="remarks"></a>Примечания  
  
-   После создания тома фокус автоматически переместится на новый том.  
  
## <a name="BKMK_examples"></a>Примеров  
Чтобы создать том размером 1000 МБ, на диске 1 введите:  
  
```  
create volume simple size=1000 disk=1  
```  
  
#### <a name="additional-references"></a>Дополнительные ссылки  
[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
  

  

