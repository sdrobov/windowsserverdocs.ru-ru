---
title: reset session
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 5a0991c76ba890bb94b0dcf258df6207ed228e72
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66441794"
---
# <a name="reset-session"></a>reset session

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Позволяет сбросить (Удалить) сеанс на сервере узла сеансов удаленных рабочих столов (rd узла сеансов).  
Примеры для использования этой команды, см. в разделе [примеры](#BKMK_examples).  

> [!NOTE]  
> В Windows Server 2008 R2 службы терминалов были переименованы на службы удаленных рабочих столов. Чтобы найти новые возможности в последней версии, см. в разделе [какие возможности служб удаленных рабочих столов в Windows Server 2012](https://technet.microsoft.com/library/hh831527) в технической библиотеке Windows Server.  

## <a name="syntax"></a>Синтаксис  
```  
reset session {<SessionName> | <SessionID>} [/server:<ServerName>] [/v]  
```  

## <a name="parameters"></a>Параметры  

|Параметр|Описание|  
|-------|--------|  
|\<Имя сеанса >|Задает имя сеанса, который вы хотите сбросить. Чтобы определить имя сеанса, используйте **запрос сеанса** команды.|  
|\<SessionID >|Указывает идентификатор сеанса для сброса.|  
|/ Server:\<ServerName >|Указывает сервер терминалов, содержащий сеанс, который вы хотите сбросить. В противном случае используется текущий сервер узла сеансов удаленных рабочих столов.|  
|/v|Отображает сведения о выполненных действиях.|  
|/?|Отображение справки в командной строке.|  

## <a name="remarks"></a>Примечания  
-   Вы всегда можете сбросить собственный сеанс, но необходимо иметь разрешение полного доступа для сброса сеанса другого пользователя.  
-   Имейте в виду, что сброс сеанса пользователя без предупреждения пользователя может привести к потере данных в сеансе.  
-   Сбросить сеанс необходимо только в случае неисправности или перестала отвечать на запросы.  
-   **/Server** параметр является обязательным только в том случае, если вы используете **сбросить настройки сеанса** с удаленного сервера.  

## <a name="BKMK_examples"></a>Примеры  
- Чтобы сбросить сеанс, обозначенный как rdp-tcp #6, введите следующую команду:  
  ```  
  reset session rdp-tcp#6  
  ```  
- Чтобы сбросить настройки сеанса, использующего код сеанса 3, введите:  
  ```  
  reset session 3  
  ```  

#### <a name="additional-references"></a>Дополнительная справка  
[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  
[Службы удаленных рабочих столов &#40;служб терминалов&#41; описанием команды](remote-desktop-services-terminal-services-command-reference.md)  
