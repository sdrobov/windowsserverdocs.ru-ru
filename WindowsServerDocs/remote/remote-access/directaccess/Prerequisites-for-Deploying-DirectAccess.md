---
title: Предварительные требования для развертывания DirectAccess
description: Этот раздел содержит необходимые компоненты для развертывания DirectAccess в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology:
- networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 57c7e039-42ef-4909-867a-b5f669c9e74e
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 09c21facd1a0242b1edbd0436e90c8ebd79f0e2d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59824175"
---
# <a name="prerequisites-for-deploying-directaccess"></a>Предварительные требования для развертывания DirectAccess

>Область применения. Windows Server (полугодовой канал), Windows Server 2016

В следующей таблице перечислены необходимые компоненты, необходимые для развертывания DirectAccess с помощью мастера настройки.  
  
|||  
|-|-|  
|Сценарий|предварительные требования|  
|[Развертывание одиночного сервера DirectAccess с помощью мастера начальной настройки](../../remote-access/directaccess/single-server-wizard/Deploy-a-Single-DirectAccess-Server-Using-the-Getting-Started-Wizard.md)|-Брандмауэра Windows должен быть включен для всех профилей<br /><br />-Поддерживается только для клиентов под управлением Windows 10&reg;, <br />              Windows&reg; 8 и Windows&reg; 8.1 Корпоративная.<br /><br />-Инфраструктура открытых ключей не является обязательным.<br /><br />-Не поддерживается для развертывания двухфакторной проверки подлинности. Для проверки подлинности требуются учетные данные домена.<br /><br />-DirectAccess автоматически развертывается на всех мобильных компьютерах в текущем домене.<br /><br />-Трафик в Интернет не проходит через DirectAccess. Конфигурация принудительного туннелирования не поддерживается.<br /><br />-Сервер DirectAccess находится сервер сетевых расположений.<br /><br />-Network Access Protection (NAP) не поддерживается.<br /><br />-Изменение политик с помощью функции консоли управления DirectAccess или командлетов Windows PowerShell не поддерживается.<br /><br />-Конфигурации с несколькими узлами, сейчас или в будущем, сначала выполните инструкции в [развертывание одиночного сервера DirectAccess с расширенными параметрами](../../remote-access/directaccess/single-server-advanced/Deploy-a-Single-DirectAccess-Server-with-Advanced-Settings.md).|  
|[Развертывание одиночного сервера DirectAccess с расширенными параметрами](../../remote-access/directaccess/single-server-advanced/Deploy-a-Single-DirectAccess-Server-with-Advanced-Settings.md)|-Инфраструктура открытых ключей должны быть развернуты.<br />    Дополнительные сведения см. в разделе [мини-модуль руководство по лаборатории тестирования: Базовая PKI для Windows Server 2012](https://social.technet.microsoft.com/wiki/contents/articles/7862.test-lab-guide-mini-module-basic-pki-for-windows-server-2012.aspx).<br /><br />-Брандмауэр Windows, должен быть включен для всех профилей.<br /><br />Поддерживают следующие операционные системы сервера DirectAccess.<br /><br />— Вы можете развернуть все версии Windows Server 2016, как клиент DirectAccess или сервера DirectAccess.<br />— Вы можете развернуть все версии Windows Server 2012 R2, как клиент DirectAccess или сервера DirectAccess.<br />— Вы можете развернуть все версии Windows Server 2012, как клиент DirectAccess или сервера DirectAccess.<br />— Вы можете развернуть все версии Windows Server 2008 R2, как клиент DirectAccess или сервера DirectAccess.<br /><br />Следующие клиентские операционные системы поддерживают DirectAccess.<br /><br />-Windows 10&reg; Enterprise<br />-Windows 10&reg; Enterprise 2015 долгосрочной перспективе Servicing Branch (LTSB)<br />-Windows&reg; 8 и 8.1 Enterprise<br />-Windows&reg; 7 Ultimate<br />-Windows&reg; 7 Корпоративная<br /><br />-Конфигурация принудительного туннелирования с помощью проверки подлинности KerbProxy не поддерживается.<br /><br />-Изменение политик с помощью функции консоли управления DirectAccess или командлетов Windows PowerShell не поддерживается.<br /><br />-Отделение NAT64/DNS64 и ролей сервера IP-HTTPS на другом сервере не поддерживается.|  
  


