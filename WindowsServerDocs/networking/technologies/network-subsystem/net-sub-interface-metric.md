---
title: Настройка порядка сетевых интерфейсов
description: Этот раздел входит руководство Настройка производительности сетевой подсистемы для Windows Server 2016.
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: 3266328c-ca82-40d2-90ca-854b7088ccaa
manager: brianlic
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 2edf9d312e50a0fd8485e0032dee8413675367cf
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="configure-the-order-of-network-interfaces"></a>Настройка порядка сетевых интерфейсов

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

В Windows Server 2016 и Windows 10 можно использовать метрики интерфейса для настройки порядка сетевых интерфейсов.

Это отличается от предыдущих версий Windows и Windows Server, которая позволяет настроить порядок привязки сетевых адаптеров с помощью пользовательского интерфейса или команды **INetCfgComponentBindings::MoveBefore** и **INetCfgComponentBindings::MoveAfter**. Эти два метода для расстановки компонентов сетевых интерфейсов недоступны в Windows Server 2016 и Windows 10.

Вместо этого можно использовать новый метод для настройки порядка перечисления сетевых адаптеров, настроив метрики интерфейса для каждого адаптера. Метрики интерфейса можно настроить с помощью [Set-NetIPInterface](https://docs.microsoft.com/en-us/powershell/module/nettcpip/set-netipinterface) команды Windows PowerShell.

Когда выбираются маршруты сетевого трафика и настройки **Метрика интерфейса** параметр **Set-NetIPInterface** команда общую метрику, используется для определения интерфейса предпочтений представляет собой сумму метрики маршрута и метрики интерфейса. Как правило метрики интерфейса предоставляет предпочтений для определенного интерфейса, например, с помощью проводного, если оба проводной и беспроводной связи, доступны.

В следующем примере команды Windows PowerShell показано использование этого параметра.

    Set-NetIPInterface -InterfaceIndex 12 -InterfaceMetric 15

Порядок адаптеров в список определяется метрики интерфейса IPv4 или IPv6.  Дополнительные сведения см. в разделе [функции GetAdaptersAddresses](https://msdn.microsoft.com/library/windows/desktop/aa365915%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396).

Ссылки на все разделы в этом руководстве в разделе [Настройка производительности сетевой подсистемы](net-sub-performance-top.md).
