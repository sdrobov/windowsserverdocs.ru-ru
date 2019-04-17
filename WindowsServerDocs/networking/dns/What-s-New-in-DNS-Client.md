---
title: Новые возможности DNS-клиента в Windows Server
description: В этом разделе представлен обзор новые возможности DNS-клиента в Windows Server и Windows 10
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking-dns
ms.topic: article
ms.assetid: 6edaba84-4595-4fd8-95d7-64d4d975a38a
ms.author: pashort
author: shortpatti
ms.openlocfilehash: defe88fe2a1e4f5393be4d5d5938d9f5bfbfb5d6
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="whats-new-in-dns-client-in-windows-server-2016"></a>Новые возможности DNS-клиента в Windows Server 2016

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

В этом разделе описываются функциональные возможности клиента доменных имен (DNS), добавленные и измененные в Windows 10 и Windows Server 2016 и более поздних версий этих операционных систем.
  
## <a name="updates-to-dns-client"></a>Обновления для DNS-клиента

**Привязка службы DNS-клиента**: В Windows 10, служба DNS-клиента обеспечивает расширенную поддержку для компьютеров с более чем одного сетевого интерфейса. Для компьютеров, многосетевой разрешение DNS оптимизирован следующими способами:  
  
-   Если DNS-сервер, настроенный на определенном интерфейсе используется для разрешения запросов DNS, служба DNS-клиент будет привязан к этот интерфейс перед отправкой запроса DNS.  
  
    Связав для определенного интерфейса, он может DNS четко указать интерфейс, где выполняется разрешение имен, Включение приложений для оптимизации взаимодействия с DNS-клиента за этот сетевой интерфейс.  
  
-   Если DNS-сервер, который используется обозначается параметр групповой политики из таблицы политики разрешения имен (NRPT), служба DNS-клиента не выполнить привязку для определенного интерфейса.  
  
> [!NOTE]  
> Изменения в службе DNS-клиента в Windows 10 также присутствуют в компьютерах под управлением Windows Server 2016 и более поздних версиях.  
  
## <a name="see-also"></a>См. также:  
  
-   [Новые возможности DNS-сервера в Windows Server 2016](What-s-New-in-DNS-Server.md)  
  

