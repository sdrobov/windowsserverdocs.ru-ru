---
title: netcfg
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 8f8368aaff16592a55cc9def84d593cf323f28ee
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71373289"
---
# <a name="netcfg"></a>netcfg

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Устанавливает среда предустановки Windows (WinPE), облегченную версию Windows, используемую для развертывания рабочих станций.   
## <a name="syntax"></a>Синтаксис  
```  
netcfg [/v] [/e] [/winpe] [/l ] /c /i  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|/v|Выполнение в подробном режиме (подробный)|  
|/e|Использование переменных среды обслуживания во время установки и удаления|  
|/винпе|Устанавливает TCP/IP, NetBIOS и Microsoft Client для предустановки Windows среды|  
|/l|Предоставляет расположение INF-файла|  
|/c|Предоставляет класс устанавливаемого компонента. Протокол, служба или клиент|  
|/i|Предоставляет идентификатор компонента|  
|/s|Предоставляет тип отображаемых компонентов<br /><br />\та = адаптеры, n = компоненты сети|  
|/?|Отображение справки в командной строке.|  
## <a name="BKMK_Examples"></a>Примеров  
Чтобы установить *Пример* протокола с помощью к:\оемдир\ексампле.инф, выполните следующие действия.  
```  
netcfg /l c:\oemdir\example.inf /c p /i example  
```  
Чтобы установить службу *MS_Server* , выполните следующие действия.  
```  
netcfg /c s /i MS_Server  
```  
Установка протокола TCP/IP, NetBIOS и Microsoft Client для среды предустановки Windows  
```  
netcfg /v /winpe  
```  
Чтобы отобразить, если компонент *MS_IPX* установлен:  
```  
netcfg /q MS_IPX  
```  
Чтобы удалить *MS_IPX*компонента, выполните следующие действия.  
```  
netcfg /u MS_IPX  
```  
Чтобы отобразить все установленные сетевые компоненты, выполните следующие действия.  
```  
netcfg /s n  
```  
Для отображения путей привязки, содержащих *MS_TCPIP*:  
```  
netcfg /b ms_tcpip  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
