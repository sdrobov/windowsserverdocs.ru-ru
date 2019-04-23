---
title: showmount
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 26acf24922e6ac53a5c902d65eb0f23bff0af93b
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59852355"
---
# <a name="showmount"></a>showmount

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Можно использовать **showmount** для отображения подключенные каталоги.  
  
## <a name="syntax"></a>Синтаксис  
```
showmount {-e|-a|-d} <Server>  
```

## <a name="description"></a>Описание  
**Showmount** команда\-строки служебная программа отображает сведения об экспорте сервером для NFS на компьютере, указанном с подключенными файловыми системами *сервера*. Если *Server* не указан, **showmount** отображает сведения о компьютере, на котором **showmount** команда.  
  
Необходимо указать один из следующих вариантов:  
  
- **\-e** -отображает все файловые системы, экспортированный на сервере.  
- **\-** -отображает все сетевой файловой системы \(NFS\) клиентов и каталогов на сервере каждого подключен.  
- **\-d** -отображаются все каталоги на сервере, на который в данный момент подключены клиенты NFS.  
  
## <a name="see-also"></a>См. также  
[Службы сетевой файл системы Справочник по командам](services-for-network-file-system-command-reference.md)  