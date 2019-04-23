---
title: Новые возможности DNS-клиента в Windows Server
description: В этом разделе представлен обзор новых возможностей в DNS-клиента в Windows Server и Windows 10
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking-dns
ms.topic: article
ms.assetid: 6edaba84-4595-4fd8-95d7-64d4d975a38a
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 34b1a64465e217fbd7e6b3ae55e89832a7a4e48c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59860565"
---
# <a name="whats-new-in-dns-client-in-windows-server-2016"></a>Новые возможности DNS-клиента в Windows Server 2016

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

В этом разделе описываются возможности клиента доменных имен (DNS), которые являются новыми или измененными в Windows 10 и Windows Server 2016 и более поздних версиях этих операционных систем.
  
## <a name="updates-to-dns-client"></a>Обновления для DNS-клиента

**Привязка службы DNS-клиент**: В Windows 10 служба DNS-клиента обеспечивает расширенную поддержку для компьютеров с более чем один сетевой интерфейс. Для компьютеров с адресацией разрешение DNS оптимизирован одним из следующих способов:  
  
-   Когда DNS-сервер, настроенный на конкретный интерфейс используется для разрешения запросов DNS, служба DNS-клиента привязывается к этому интерфейсу перед отправкой запроса DNS.  
  
    Путем привязки на конкретный интерфейс, он может DNS четко укажите интерфейс, где происходит разрешение имен, Включение приложений для оптимизации связь с DNS-клиент за этот сетевой интерфейс.  
  
-   Если DNS-сервер, который используется с помощью параметра групповой политики из таблицы политики разрешения имен (NRPT), служба DNS-клиента не обеспечивает и привязку к конкретному интерфейсу.  
  
> [!NOTE]  
> Изменения в службе клиента DNS в Windows 10 также присутствуют в компьютерах под управлением Windows Server 2016 и более поздних версий.  
  
## <a name="see-also"></a>См. также  
  
-   [Новые возможности DNS-сервера в Windows Server 2016](What-s-New-in-DNS-Server.md)  
  

