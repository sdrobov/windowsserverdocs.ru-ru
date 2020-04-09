---
title: reset session
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4f029ecc-874e-415a-95a8-8b731bae35f9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: b83aa67e0d90be9ddc679b32c8ffa4270efec41f
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80835797"
---
# <a name="reset-session"></a>reset session

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Позволяет сбросить (удалить) сеанс на сервере узла сеансов удаленный рабочий стол (на узле сеансов удаленных рабочих столов).  
Примеры использования этой команды см. в разделе [примеры](#BKMK_examples).  

> [!NOTE]  
> В Windows Server 2008 R2 службы терминалов называются службами удаленных рабочих столов. Чтобы узнать о новых возможностях последней версии, см. статью [новые возможности службы удаленных рабочих столов в Windows server 2012](https://technet.microsoft.com/library/hh831527) в библиотеке TechNet по Windows Server.  

## <a name="syntax"></a>Синтаксис  
```  
reset session {<SessionName> | <SessionID>} [/server:<ServerName>] [/v]  
```  

### <a name="parameters"></a>Параметры  

|Параметр|Описание|  
|-------|--------|  
|\<SessionName >|Указывает имя сеанса, который требуется сбросить. Чтобы определить имя сеанса, используйте команду **запроса сеанса** .|  
|\<SessionID >|Указывает идентификатор сеанса для сброса.|  
|/Server:\<ServerName >|Указывает сервер терминалов, содержащий сеанс, который требуется сбросить. В противном случае используется текущий сервер узла сеансов удаленных рабочих столов.|  
|/v|Отображает сведения о выполняемых действиях.|  
|/?|Отображает справку в командной строке.|  

## <a name="remarks"></a>Примечания  
-   Вы всегда можете сбросить собственные сеансы, но для сброса сеанса другого пользователя необходимо иметь разрешение «Полный доступ».  
-   Имейте в виду, что сброс сеанса пользователя без предупреждения пользователь может привести к утрате данных в сеансе.  
-   Сброс сеанса следует выполнять только в том случае, если он неисправен или перестал отвечать на запросы.  
-   Параметр **/Server** требуется только при использовании параметра **сбросить сеанс** с удаленного сервера.  

## <a name="examples"></a><a name=BKMK_examples></a>Примеров  
- Чтобы сбросить сеанс с назначенным RDP-TCP # 6, введите:  
  ```  
  reset session rdp-tcp#6  
  ```  
- Чтобы сбросить сеанс, использующий сеанс с ИДЕНТИФИКАТОРом 3, введите:  
  ```  
  reset session 3  
  ```  

## <a name="additional-references"></a>Дополнительные материалы  
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
[Справочник по командам служб удаленных рабочих столов (служб терминалов)](remote-desktop-services-terminal-services-command-reference.md)  
