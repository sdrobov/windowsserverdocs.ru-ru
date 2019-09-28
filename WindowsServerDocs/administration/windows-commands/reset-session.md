---
title: reset session
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4f029ecc-874e-415a-95a8-8b731bae35f9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: 67a4e910ba87209c9700f2242f7859a6cc9e725f
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71384530"
---
# <a name="reset-session"></a>reset session

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Позволяет сбросить (удалить) сеанс на сервере узла сеансов удаленный рабочий стол (на узле сеансов удаленных рабочих столов).  
Примеры использования этой команды см. в разделе [примеры](#BKMK_examples).  

> [!NOTE]  
> В Windows Server 2008 R2 службы терминалов были переименованы на службы удаленных рабочих столов. Чтобы узнать о новых возможностях последней версии, см. статью [новые возможности службы удаленных рабочих столов в Windows server 2012](https://technet.microsoft.com/library/hh831527) в библиотеке TechNet по Windows Server.  

## <a name="syntax"></a>Синтаксис  
```  
reset session {<SessionName> | <SessionID>} [/server:<ServerName>] [/v]  
```  

## <a name="parameters"></a>Параметры  

|Параметр|Описание|  
|-------|--------|  
|@no__t 0SessionName >|Указывает имя сеанса, который требуется сбросить. Чтобы определить имя сеанса, используйте команду **запроса сеанса** .|  
|@no__t 0SessionID >|Указывает идентификатор сеанса для сброса.|  
|/Server: @no__t 0ServerName >|Указывает сервер терминалов, содержащий сеанс, который требуется сбросить. В противном случае используется текущий сервер узла сеансов удаленных рабочих столов.|  
|/v|Отображает сведения о выполняемых действиях.|  
|/?|Отображение справки в командной строке.|  

## <a name="remarks"></a>Примечания  
-   Вы всегда можете сбросить собственные сеансы, но для сброса сеанса другого пользователя необходимо иметь разрешение «Полный доступ».  
-   Имейте в виду, что сброс сеанса пользователя без предупреждения пользователь может привести к утрате данных в сеансе.  
-   Сброс сеанса следует выполнять только в том случае, если он неисправен или перестал отвечать на запросы.  
-   Параметр **/Server** требуется только при использовании параметра **сбросить сеанс** с удаленного сервера.  

## <a name="BKMK_examples"></a>Примеров  
- Чтобы сбросить сеанс с назначенным RDP-TCP # 6, введите:  
  ```  
  reset session rdp-tcp#6  
  ```  
- Чтобы сбросить сеанс, использующий сеанс с ИДЕНТИФИКАТОРом 3, введите:  
  ```  
  reset session 3  
  ```  

#### <a name="additional-references"></a>Дополнительная справка  
[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
[Справочник &#40;по командам служб&#41; терминалов службы удаленных рабочих столов](remote-desktop-services-terminal-services-command-reference.md)  
