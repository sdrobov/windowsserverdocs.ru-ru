---
title: Настройка порядка сетевых интерфейсов
description: Этот раздел является частью руководства по настройке производительности сетевой подсистемы Windows Server 2016.
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: 3266328c-ca82-40d2-90ca-854b7088ccaa
manager: brianlic
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 18bc9a268b4e69e4b87b6b1e310f1162473adb10
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59821775"
---
# <a name="configure-the-order-of-network-interfaces"></a>Настройка порядка сетевых интерфейсов

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

В Windows Server 2016 и Windows 10 можно использовать метрики интерфейса для настройки порядка сетевых интерфейсов.

Это отличается от в предыдущих версиях Windows и Windows Server, который позволял настроить порядок привязки сетевых адаптеров с помощью пользовательского интерфейса или команды **INetCfgComponentBindings::MoveBefore**и **INetCfgComponentBindings::MoveAfter**. Эти два метода для упорядочения сетевых интерфейсов недоступны в Windows Server 2016 и Windows 10.

Вместо этого можно использовать новый метод для настройки перечисляемых порядок сетевых адаптеров, настроив метрики интерфейса каждого адаптера. Метрики интерфейса можно настроить с помощью [Set-NetIPInterface](https://docs.microsoft.com/powershell/module/nettcpip/set-netipinterface) команду Windows PowerShell.

Когда выбираются маршруты сетевого трафика и настройки **Метрика интерфейса** параметр **Set-NetIPInterface** команды общую метрику, используется для определения интерфейса приоритет — сумма метрики маршрута и метрики интерфейса. Как правило метрики интерфейса отдает предпочтение методам, определенный интерфейс, например с помощью проводного, если оба проводной и беспроводной связи доступны.

В следующем примере команды Windows PowerShell показано использование этого параметра.

    Set-NetIPInterface -InterfaceIndex 12 -InterfaceMetric 15

Метрики интерфейса IPv4 или IPv6, определяется порядок, в котором адаптеры будут отображаться в списке.  Дополнительные сведения см. в разделе [GetAdaptersAddresses функция](https://msdn.microsoft.com/library/windows/desktop/aa365915%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396).

Ссылки на все разделы в этом руководстве, см. в разделе [Настройка производительности сетевой подсистемы](net-sub-performance-top.md).
