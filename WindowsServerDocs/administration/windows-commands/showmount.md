---
title: showmount
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a6dd562e-e3bd-4ee6-be3b-6d29e29fd20e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e1d197072db93130de880b5ec52d1875720b1d26
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71383910"
---
# <a name="showmount"></a>showmount

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Для просмотра подключенных каталогов можно использовать **шовмаунт** .  
  
## <a name="syntax"></a>Синтаксис  
```
showmount {-e|-a|-d} <Server>  
```

## <a name="description"></a>Описание  
Служебная программа **шовмаунт** Command @ no__t-1line отображает сведения о подключенных файловых системах, экспортированных сервером для NFS на компьютере, указанном *сервером*. Если *сервер* не указан, **шовмаунт** отображает сведения о компьютере, на котором выполняется команда **шовмаунт** .  
  
Необходимо указать один из следующих параметров:  
  
- **\-E** -отображает все файловые системы, экспортированные на сервере.  
- **\-A** — отображает все клиенты сетевой файловой системы \(NFS @ no__t-3 и каталоги на сервере, на котором они подключены.  
- **\-d** — отображает все каталоги на сервере, которые в настоящее время подключены клиентами NFS.  
  
## <a name="see-also"></a>См. также  
[Справочник по командам служб для NFS](services-for-network-file-system-command-reference.md)  