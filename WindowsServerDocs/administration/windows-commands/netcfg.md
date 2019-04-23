---
title: netcfg
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e2daaab7-12db-4e36-b70c-db8906d084f7 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: aed535f843da6d735526ea97c07f94564dc00dc6
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59871325"
---
# <a name="netcfg"></a>netcfg

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Устанавливает среду предустановки Windows (WinPE), это упрощенная версия Windows, используемая для развертывания рабочих станций.   
## <a name="syntax"></a>Синтаксис  
```  
netcfg [/v] [/e] [/winpe] [/l ] /c /i  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|/v|Запустить в режиме подробного протоколирования (детализация)|  
|/e|Использование обслуживания переменных среды во время установки и удаления|  
|/WinPE|Устанавливает TCP/IP, NetBIOS и клиент Microsoft для среды предустановки Windows|  
|/l|Предоставляет расположение INF|  
|/c|Предоставляет класс компонента должен быть установлен; протокол, службы или клиента|  
|/i|Содержит идентификатор компонента|  
|/s|Предоставляет тип компоненты для отображения<br /><br />\ta = адаптеров, n = net компонентов|  
|/?|Отображение справки в командной строке.|  
## <a name="BKMK_Examples"></a>Примеры  
Для установки протокола *пример* с помощью c:\oemdir\example.inf:  
```  
netcfg /l c:\oemdir\example.inf /c p /i example  
```  
Чтобы установить *MS_Server* службы:  
```  
netcfg /c s /i MS_Server  
```  
Чтобы установить TCP/IP, NetBIOS и клиент Microsoft для среды предустановки Windows  
```  
netcfg /v /winpe  
```  
Для отображения, если компонент *MS_IPX* установлен:  
```  
netcfg /q MS_IPX  
```  
Чтобы удалить компонент *MS_IPX*:  
```  
netcfg /u MS_IPX  
```  
Чтобы показать все компоненты net.  
```  
netcfg /s n  
```  
Для привязки пути, содержащие показано *MS_TCPIP*:  
```  
netcfg /b ms_tcpip  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
