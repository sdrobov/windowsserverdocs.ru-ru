---
title: FTP open_1
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4b61926a-dc60-4b4c-96d3-64e5c91c18ba vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: da7926914e2cbdbb4909093d90c33025ae5cd695
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59882475"
---
# <a name="ftp-open1"></a>FTP: open_1

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Подключается к указанной FTP-сервера.   
## <a name="syntax"></a>Синтаксис  
```  
open <computer> [<Port>]  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|<computer>|Указывает удаленный компьютер, к которому вы пытаетесь подключиться.|  
|[<Port>]|Указывает номер порта TCP для подключения к серверу ftp. По умолчанию используется TCP-порт 21.|  
## <a name="remarks"></a>Примечания  
IP-адрес или имя (в этом случае DNS-сервер или файл Hosts должны быть доступны) можно использовать для указания **компьютера**.  
## <a name="BKMK_Examples"></a>Примеры  
Подключение к серверу ftp по адресу **ftp.microsoft.com**.  
```  
Open ftp.microsoft.com  
```  
Подключение к серверу ftp по адресу **ftp.microsoft.com** прослушивает TCP-порт 755.  
```  
open ftp.microsoft.com 755  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
