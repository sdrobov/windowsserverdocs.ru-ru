---
title: Предварительные требования для развертывания DirectAccess
description: В этом разделе приводятся предварительные требования для развертывания DirectAccess в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 57c7e039-42ef-4909-867a-b5f669c9e74e
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 6e04dbf1576277493ec849c8de82aeab51e97649
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71388815"
---
# <a name="prerequisites-for-deploying-directaccess"></a>Предварительные требования для развертывания DirectAccess

>Область применения. Windows Server (Semi-Annual Channel), Windows Server 2016

В следующей таблице перечислены предварительные требования, необходимые для использования мастеров настройки для развертывания DirectAccess.  
  
|||  
|-|-|  
|Сценарий|Предварительные требования|  
|[Развертывание одного сервера DirectAccess с помощью мастера начало работы](../../remote-access/directaccess/single-server-wizard/Deploy-a-Single-DirectAccess-Server-Using-the-Getting-Started-Wizard.md)|— Брандмауэр Windows должен быть включен для всех профилей.<br /><br />— Поддерживается только для клиентов, работающих под управлением Windows 10 @ no__t-0, <br />              Windows @ no__t-0 8 и Windows @ no__t-1 8,1 Enterprise.<br /><br />— Инфраструктура открытых ключей не требуется.<br /><br />— Не поддерживается для развертывания двухфакторной проверки подлинности. Для проверки подлинности требуются учетные данные домена.<br /><br />— Автоматически развертывает DirectAccess на всех мобильных компьютерах в текущем домене.<br /><br />— Трафик к Интернету не проходит через DirectAccess. Конфигурация принудительного туннелирования не поддерживается.<br /><br />— Сервер DirectAccess — это сервер сетевых расположений.<br /><br />— Защита доступа к сети (NAP) не поддерживается.<br /><br />-Изменение политик с помощью компонента, отличного от консоли управления DirectAccess или командлетов Windows PowerShell, не поддерживается.<br /><br />— Для многосайтовой конфигурации, сейчас или в будущем, сначала следуйте указаниям в статье [развертывание одного сервера DirectAccess с дополнительными параметрами](../../remote-access/directaccess/single-server-advanced/Deploy-a-Single-DirectAccess-Server-with-Advanced-Settings.md).|  
|[Развертывание одного сервера DirectAccess с расширенными параметрами](../../remote-access/directaccess/single-server-advanced/Deploy-a-Single-DirectAccess-Server-with-Advanced-Settings.md)|— Инфраструктура открытых ключей должна быть развернута.<br />    Дополнительные сведения см. в разделе [Test Lab Guide мини-модуль: Базовый PKI для Windows Server 2012 @ no__t-0.<br /><br />— Брандмауэр Windows должен быть включен для всех профилей.<br /><br />Следующие серверные операционные системы поддерживают DirectAccess.<br /><br />— Можно развернуть все версии Windows Server 2016 в качестве клиента DirectAccess или сервера DirectAccess.<br />— Можно развернуть все версии Windows Server 2012 R2 в качестве клиента DirectAccess или сервера DirectAccess.<br />— Можно развернуть все версии Windows Server 2012 в качестве клиента DirectAccess или сервера DirectAccess.<br />— Можно развернуть все версии Windows Server 2008 R2 в качестве клиента DirectAccess или сервера DirectAccess.<br /><br />Следующие клиентские операционные системы поддерживают DirectAccess.<br /><br />— Windows 10 @ no__t-0 Корпоративная<br />— Windows 10 @ no__t-0 Enterprise 2015 Long Term Servicing Branch (LTSB)<br />— Windows @ no__t-0 8 и 8,1 Enterprise<br />-Windows @ no__t-0 7 Максимальная<br />-Windows @ no__t-0 7 Корпоративная<br /><br />— Конфигурация принудительного туннелирования не поддерживается при проверке подлинности Кербпрокси.<br /><br />-Изменение политик с помощью компонента, отличного от консоли управления DirectAccess или командлетов Windows PowerShell, не поддерживается.<br /><br />-Разделение ролей NAT64, DNS64 и IPHTTPS сервера на другом сервере не поддерживается.|  
  


