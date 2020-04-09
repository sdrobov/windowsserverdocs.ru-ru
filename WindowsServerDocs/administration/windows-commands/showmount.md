---
title: showmount
description: Раздел команд Windows для шовмаунт, в котором отображаются подключенные каталоги.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a6dd562e-e3bd-4ee6-be3b-6d29e29fd20e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6fa61d47bb14cf21d93beec0a6e9257b9f66737b
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80834227"
---
# <a name="showmount"></a>showmount

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Для просмотра подключенных каталогов можно использовать **шовмаунт** .  
  
## <a name="syntax"></a>Синтаксис  
```
showmount {-e|-a|-d} <Server>  
```

## <a name="description"></a>Описание  
Программа командной строки **шовмаунт**\-Line отображает сведения о подключенных файловых системах, экспортированных сервером для NFS на компьютере, указанном *сервером*. Если *сервер* не указан, **шовмаунт** отображает сведения о компьютере, на котором выполняется команда **шовмаунт** .  
  
Необходимо указать один из следующих параметров:  
  
- **\-e** — отображает все файловые системы, экспортированные на сервере.  
- **\-a** — отображает все сетевые файловые системы \(NFS\) клиенты и каталоги на сервере, которые подключены.  
- **\-d** — отображает все каталоги на сервере, которые в настоящее время подключены клиентами NFS.  
  
## <a name="see-also"></a>См. также  
[Справочник по командам служб для NFS](services-for-network-file-system-command-reference.md)  