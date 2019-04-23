---
ms.assetid: ''
title: Insider preview возможностей службы времени Windows в Windows Server 2019
description: Новые возможности службы времени Windows в Windows Server 2019
author: shortpatti
ms.author: pashort
ms.date: 09/05/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: networking
ms.openlocfilehash: ef0ff317f5957add5ecbe9f88ef83753b805ec41
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59829025"
---
# <a name="insider-preview"></a>Insider Preview 


## <a name="leap-second-support"></a>Поддержка секунда


>Относится к: Windows Server 2019 и Windows 10, версия 1809

Секунда — это 1 секунда корректировку время от времени в формате UTC. Как замедления вращения земли, [UTC](https://en.wikipedia.org/wiki/Coordinated_Universal_Time) (atomic шкала времени) отличается от [среднее время хиджры](https://en.wikipedia.org/wiki/Solar_time#Mean_solar_time) или для выполнения астрономических времени.  После UTC различаются по более.9 секунд [секунда](https://en.wikipedia.org/wiki/Leap_second) вставляется синхронизировать UTC в среднее время хиджры.

Корректировочных секунд стали важным в соответствии с точностью и нормативных требований отслеживания в США и ЕС.

Дополнительные сведения см. в следующих разделах:

-  Наши [блоге объявлений](https://blogs.technet.microsoft.com/networking/2018/07/18/top10-ws2019-hatime/)

-  Руководство по проверке для [разработчиков](https://aka.ms/Dev-LeapSecond)

-  Руководство по проверке для [ИТ-специалистов](https://aka.ms/ITPro-LeapSecond)


## <a name="precision-time-protocol"></a>Протокол точности времени

>Относится к: Windows Server 2019 и Windows 10, версия 1809

Новый поставщик времени, включенных в Windows Server 2019 и Windows 10 (версия 1809) позволяет выполнять синхронизацию времени с помощью протокола точности времени (PTP). Как время распределяет по сети, обнаружении delay (задержка), которая, если не учитываются, или если это не симметричного, становится все труднее понять отметку времени, отправленных сервером времени. PTP позволяет сетевых устройств добавить задержки, вызванной каждое сетевое устройство в измерений времени, тем самым обеспечивая гораздо более точные Образец времени на клиенте windows.

Дополнительные сведения см. в следующих разделах:

-  Наши [блоге объявлений](https://blogs.technet.microsoft.com/networking/2018/07/18/top10-ws2019-hatime/)

-  Руководство по проверке для [ИТ-специалистов](https://aka.ms/PTPValidation)


## <a name="software-timestamping"></a>Установка меток времени программного обеспечения

>Относится к: Windows Server 2019 и Windows 10, версия 1809

При получении пакета синхронизации с сервером времени по сети, он должен обрабатываться сетевой стек ОС перед потребляются через службу времени. Каждый компонент в сетевом стеке вводит переменный объем задержки, которая влияет на точность измерения времени.

![Установка меток времени программного обеспечения](../media/Windows-Time-Service/software-timestamping.png)

Чтобы решить эту проблему, штампов времени программного обеспечения позволяет нам timestamp пакетов до и после выполнения «Windows Networking компонентов» выше, чтобы учитывать такую задержку в операционной системе.

Дополнительные сведения см. в следующих разделах:

-  Наши [блоге объявлений](https://blogs.technet.microsoft.com/networking/2018/07/18/top10-ws2019-hatime/)

-  Руководство по проверке для [ИТ-специалистов](https://github.com/Microsoft/SDN/blob/master/FeatureGuide/Validation%20Guide%20-%20RS5%20-%20Software%20Timestamping.docx)



---