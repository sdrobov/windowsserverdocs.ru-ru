---
title: изменение
description: Команды Windows для изменения, которые изменяют удаленный рабочий стол параметры сервера узла сеансов для входа в систему, сопоставления COM-портов и режима установки.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 90012116-0fb3-4f34-a819-cf4d4b4f8981
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d5d91f8d0941fc96e776c761b9c7037e58588df8
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80847957"
---
# <a name="change"></a>изменение

> Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменения удаленный рабочий стол параметры сервера узла сеансов для входа в систему, сопоставления COM-портов и режима установки.

> [!NOTE]
> В Windows Server 2008 R2 службы терминалов называются службами удаленных рабочих столов. Чтобы узнать о новых возможностях последней версии, см. статью [новые возможности службы удаленных рабочих столов в Windows server 2012](https://technet.microsoft.com/library/hh831527) в библиотеке TechNet по Windows Server.

## <a name="syntax"></a>Синтаксис

 ```
 change logon
 change port
 change user
 ```
 
 ### <a name="parameters"></a>Параметры
 
 |            Параметр            |                                                   Описание                                                   |
 |---------------------------------|-----------------------------------------------------------------------------------------------------------------|
 | [change logon](change-logon.md) | Включает или отключает вход из сеансов клиента на сервере узла сеансов удаленных рабочих столов или отображает текущее состояние входа. |
 |  [change port](change-port.md)  |                перечисление или изменение сопоставления COM-портов для совместимости с приложениями MS-DOS.                |
 |  [change user](change-user.md)  |                            изменяет режим установки для сервера узла сеансов удаленных рабочих столов.                             |
 
 ## <a name="additional-references"></a>Дополнительные материалы
 - [Командная строка синтаксиса командной строки](command-line-syntax-key.md)
 [службы удаленных рабочих столов (службы терминалов) Справочник по командам](remote-desktop-services-terminal-services-command-reference.md)
