---
ms.assetid: ''
title: Предварительный просмотр функций службы времени Windows в Windows Server 2019
description: Новые функции службы времени Windows в Windows Server 2019
author: shortpatti
ms.author: pashort
ms.date: 09/05/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: networking
ms.openlocfilehash: a0c4d01d095e8052a2192d6b6352732a6fe60919
ms.sourcegitcommit: f6490192d686f0a1e0c2ebe471f98e30105c0844
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70871791"
---
# <a name="insider-preview"></a>Insider Preview 


## <a name="leap-second-support"></a>Поддержка LEAP


>Относится к: Windows Server 2019 и Windows 10, версия 1809

Високосная секунда — это случайная корректировка в формате UTC с 1 секундой. По мере того, как вращается вращение Земли, время в [формате UTC](https://en.wikipedia.org/wiki/Coordinated_Universal_Time) (атомарная шкала времени) отличается от [среднего времени на солнечное](https://en.wikipedia.org/wiki/Solar_time#Mean_solar_time) или осваивается время.  Когда время в формате UTC рассходится не более чем в .9 секундах, будет вставлена [LEAP-секунда](https://en.wikipedia.org/wiki/Leap_second) , позволяющая синхронизировать время в формате UTC с средним временем солнечного времени.

Високосные секунды стали важны для удовлетворения требований к точности и отслеживаемости в соответствии с нормативными требованиями как в США, так и в Европейского союза.

Дополнительные сведения можно найти в разделе

-  [Блог нашего объявления](https://blogs.technet.microsoft.com/networking/2018/07/18/top10-ws2019-hatime/)

-  Рекомендации по проверке для [разработчиков](https://aka.ms/Dev-LeapSecond)

-  Рекомендации по проверке для [ИТ](https://aka.ms/ITPro-LeapSecond)


## <a name="precision-time-protocol"></a>Протокол времени точности

>Относится к: Windows Server 2019 и Windows 10, версия 1809

Новый поставщик времени, входящий в Windows Server 2019 и Windows 10 (версия 1809), позволяет синхронизировать время с помощью протокола времени с точностью (PTP). По мере распределения времени по сети возникает задержка (задержка), которая, если не учитывается, или если она не является симметричной, становится все труднее понять отметку времени, отправленную с сервера времени. PTP позволяет сетевым устройствам добавить задержку, появившуюся в каждом сетевом устройстве, в измерения времени, обеспечивая более точную выборку времени для клиента Windows.

Дополнительные сведения можно найти в разделе

-  [Блог нашего объявления](https://blogs.technet.microsoft.com/networking/2018/07/18/top10-ws2019-hatime/)

-  Рекомендации по проверке для [ИТ](https://aka.ms/PTPValidation)


## <a name="software-timestamping"></a>Отметка времени программного обеспечения

>Относится к: Windows Server 2019 и Windows 10, версия 1809

При получении пакета времени по сети с сервера времени он должен быть обработан стеком сети операционной системы, прежде чем он будет использован в службе времени. Каждый компонент в стеке сети представляет собой переменный объем задержки, влияющий на точность измерения времени.

![отметка времени программного обеспечения](../media/Windows-Time-Service/software-timestamping.png)

Чтобы устранить эту проблему, отметка времени программного обеспечения позволяет отметок времени до и после "сетевых компонентов Windows", показанных выше, для учета задержки в операционной системе.

Дополнительные сведения можно найти в разделе

-  [Блог нашего объявления](https://blogs.technet.microsoft.com/networking/2018/07/18/top10-ws2019-hatime/)

-  Рекомендации по проверке для [ИТ](https://github.com/Microsoft/SDN/blob/master/FeatureGuide/Validation%20Guide%20-%20RS5%20-%20Software%20Timestamping.docx)



---