---
title: Поддерживаемых гостевых ОС Windows для Hyper-V в Windows Server
description: Список операционных систем Windows, поддерживаемых для использования в качестве гостевых на виртуальной машине. Также ссылки на статьи, близкие к для предыдущих версий Hyper-V.
ms.prod: windows-server-threshold
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 06b35897-2192-48b7-8c2d-125c520b0786
author: lizap
ms.author: elizapo
ms.date: 01/08/2019
ms.openlocfilehash: 5f0e91f3202f09d340154b49408c56752a9de577
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59874215"
---
# <a name="supported-windows-guest-operating-systems-for-hyper-v-on-windows-server"></a>Поддерживаемых гостевых ОС Windows для Hyper-V в Windows Server

>Область применения. Windows Server 2016, Windows Server 2019 г.

Hyper-V поддерживает несколько версий Windows Server, Windows и Linux дистрибутивов, выполняемых на виртуальных машинах, в качестве гостевых операционных систем. В этой статье рассматриваются поддерживаемые Windows Server и операционных системах Windows. Для дистрибутивов Linux и FreeBSD, см. в разделе [виртуальных машин поддерживается Linux и FreeBSD для Hyper-V в Windows](Supported-Linux-and-FreeBSD-virtual-machines-for-Hyper-V-on-Windows.md).  
    
Некоторые операционные системы имеют встроенные службы интеграции. Другие требуют установки или обновление служб integration services как отдельный шаг после настройки операционной системы на виртуальной машине. Дополнительные сведения см. в следующих разделах и [служб Integration Services](https://docs.microsoft.com/virtualization/hyper-v-on-windows/reference/integration-services).  
  
## <a name="supported-windows-server-guest-operating-systems"></a>Поддерживаемые гостевые операционные системы Windows Server  

Ниже перечислены версии Windows Server, поддерживаются как гостевые операционные системы для Hyper-V в Windows Server 2016 и Windows Server 2019. 
  
|Операционная система на виртуальной машине (сервер)|Максимальное число виртуальных процессоров.|Службы интеграции|Примечания|  
|-------------------------------------|----------------------------------------|------------------------|---------|  
|Windows Server 2019 |240 для поколения 2;<br>64 для поколения 1|Встроенные методы|| 
|Windows Server 2016 |240 для поколения 2;<br>64 для поколения 1|Встроенные методы|| 
|Windows Server 2012 R2 |64|Встроенные методы||  
|Windows Server 2012 |64|Встроенные методы||  
|Windows Server 2008 R2 с пакетом обновления 1 (SP1)|64|Установите все важные обновления Windows, после настройки гостевой операционной системы.|Выпуски Datacenter, Enterprise, Standard и Web.|
|Windows Server 2008 с пакетом обновления 2 (SP2)|8|Установите все важные обновления Windows, после настройки гостевой операционной системы.|Выпуски Datacenter, Enterprise, Standard и Web (32-разрядные и 64-разрядные).|  
  
## <a name="supported-windows-client-guest-operating-systems"></a>Поддерживаемые операционные системы Windows клиента гостя  

Ниже перечислены версии клиента Windows, которые поддерживаются как гостевые операционные системы для Hyper-V в Windows Server 2016 и Windows Server 2019.
  
|Операционная система на виртуальной машине (клиент)|Максимальное число виртуальных процессоров.|Службы интеграции|Примечания|  
|-------------------------------------|----------------------------------------|------------------------|---------|  
|Windows 10|32|Встроенные методы||  
|Windows 8.1|32|Встроенные методы||  
|Windows 7 с пакетом обновления 1 (SP1)|4|Обновите службы интеграции после настройки гостевой операционной системы.|Выпуски Максимальная, Корпоративная и Профессиональная (32-разрядные и 64-разрядные).|  
  
## <a name="guest-operating-system-support-on-other-versions-of-windows"></a>Поддержка гостевых операционных систем в других версиях Windows  

В следующей таблице приведены ссылки на сведения о гостевые операционные системы для Hyper-V в других версиях Windows.  
  
|Операционной системы|Раздел|  
|-------------------------|---------|  
|Windows 10|[Поддерживаемые гостевые операционные системы для клиент Hyper-V в Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/about/supported-guest-os)|  
|Windows Server 2012 R2 и Windows 8.1|-   [Windows, поддерживаемых операционных систем на виртуальных машинах для Hyper-V в Windows Server 2012 R2 и Windows 8.1](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn792027(v=ws.11))<br />-   [Linux и виртуальные машины FreeBSD в Hyper-V](Supported-Linux-and-FreeBSD-virtual-machines-for-Hyper-V-on-Windows.md)|  
|Windows Server 2012 и Windows 8|[Windows, поддерживаемых операционных систем на виртуальных машинах для Hyper-V в Windows Server 2012 и Windows 8](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn792028(v=ws.11))|  
|Windows Server 2008 и Windows Server 2008 R2|[О виртуальных машинах и гостевых операционных систем](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc794868(v=ws.10))|  
  
## <a name="how-microsoft-provides-support-for-guest-operating-systems"></a>Как корпорация Майкрософт обеспечивает поддержку гостевых операционных систем  

Корпорация Майкрософт обеспечивает поддержку гостевых операционных систем следующим образом:  
  
-   Устранение проблем, обнаруженных в операционных системах Майкрософт и в службах интеграции, поддерживается службой технической поддержки Майкрософт.  
  
-   Поддержка по проблемам в других операционных системах, сертифицированных поставщиком операционной системы для выполнения в Hyper-V, обеспечивается поставщиком.  
  
-   Если обнаруживаются проблемы в других операционных системах, корпорация Майкрософт отправляет описание проблемы в сообщество по оказанию поддержки, состоящее из множества поставщиков, [TSANet](https://www.tsanet.org/).  
  
## <a name="see-also"></a>См. также  
  
-   [Linux и виртуальные машины FreeBSD в Hyper-V](Supported-Linux-and-FreeBSD-virtual-machines-for-Hyper-V-on-Windows.md)  
  
-   [Поддерживаемые гостевые операционные системы для клиент Hyper-V в Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/about/supported-guest-os)  
  



