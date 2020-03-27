---
title: Новые возможности DNS-клиента в Windows Server
description: В этом разделе приводятся общие сведения о новых возможностях DNS-клиента в Windows Server и Windows 10.
manager: brianlic
ms.prod: windows-server
ms.technology: networking-dns
ms.topic: article
ms.assetid: 6edaba84-4595-4fd8-95d7-64d4d975a38a
ms.author: lizross
author: eross-msft
ms.openlocfilehash: a02aea149a658be2696195a2a17429b506dec1fa
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80317986"
---
# <a name="whats-new-in-dns-client-in-windows-server-2016"></a>Новые возможности DNS-клиента в Windows Server 2016

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

В этом разделе описываются функциональные возможности клиента службы доменных имен (DNS), новые или измененные в Windows 10 и Windows Server 2016 и более поздних версиях этих операционных систем.
  
## <a name="updates-to-dns-client"></a>Обновления DNS-клиента

**Привязка службы клиента DNS**. в Windows 10 служба DNS-клиента предлагает улучшенную поддержку компьютеров с несколькими сетевыми интерфейсами. Для многосетевых компьютеров разрешение DNS оптимизируется следующими способами.  
  
-   Когда DNS-сервер, настроенный на определенном интерфейсе, используется для разрешения DNS-запроса, служба DNS-клиента будет привязана к этому интерфейсу перед отправкой запроса DNS.  
  
    При привязке к определенному интерфейсу DNS-клиент может четко указать интерфейс, где происходит разрешение имен, что позволяет приложениям оптимизировать взаимодействие с DNS-клиентом через этот сетевой интерфейс.  
  
-   Если используемый DNS-сервер назначен параметром групповая политика из таблица политики разрешения имен (NRPT), то служба DNS-клиента не привязывается к конкретному интерфейсу.  
  
> [!NOTE]  
> Изменения в службе DNS-клиента в Windows 10 также существуют на компьютерах под управлением Windows Server 2016 и более поздних версий.  
  
## <a name="see-also"></a>См. также:  
  
-   [Новые возможности DNS-сервера в Windows Server 2016](What-s-New-in-DNS-Server.md)  
  

