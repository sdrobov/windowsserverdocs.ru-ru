---
title: Поддерживаемые гостевые операционные системы Windows для Hyper-V в Windows Server
description: Список операционных систем Windows, поддерживаемых для использования в качестве гостя на виртуальной машине. Также содержит ссылки на похожие статьи для предыдущих версий Hyper-V.
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.topic: article
ms.assetid: 06b35897-2192-48b7-8c2d-125c520b0786
author: lizap
ms.author: elizapo
ms.date: 01/08/2019
ms.openlocfilehash: 34183deefef3eea94c2b1da8dcb111c2c17efd8a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80857977"
---
# <a name="supported-windows-guest-operating-systems-for-hyper-v-on-windows-server"></a>Поддерживаемые гостевые операционные системы Windows для Hyper-V в Windows Server

>Область применения: Windows Server 2016, Windows Server 2019

Hyper-V поддерживает несколько версий дистрибутивов Windows Server, Windows и Linux для работы на виртуальных машинах в качестве гостевых операционных систем. В этой статье рассматриваются поддерживаемые операционные системы Windows Server и гостевые ОС Windows. Сведения о дистрибутивах Linux и FreeBSD см. [в статье Поддерживаемые виртуальные машины Linux и FreeBSD для Hyper-V в Windows](Supported-Linux-and-FreeBSD-virtual-machines-for-Hyper-V-on-Windows.md).  
    
Некоторые операционные системы имеют встроенные службы Integration Services. Для других требуется установить или обновить службы Integration Services как отдельный шаг после настройки операционной системы на виртуальной машине. Дополнительные сведения см. в разделах ниже и [Integration Services](https://docs.microsoft.com/virtualization/hyper-v-on-windows/reference/integration-services).  
  
## <a name="supported-windows-server-guest-operating-systems"></a>Поддерживаемые гостевые операционные системы Windows Server  

Ниже приведены версии Windows Server, которые поддерживаются в качестве гостевых операционных систем для Hyper-V в Windows Server 2016 и Windows Server 2019. 
  
|Операционная система на виртуальной машине (сервер)|Максимальное число виртуальных процессоров.|Службы интеграции|Примечания|  
|-------------------------------------|----------------------------------------|------------------------|---------| 
|Windows Server, версия 1909 |240 для поколения 2;<br>64 для поколения 1|Встроенные методы|Для поддержки более 240 виртуальных процессоров требуется Windows Server, версия 1903 или более поздняя гостевая операционная система.| 
|Windows Server версии 1903 |240 для поколения 2;<br>64 для поколения 1|Встроенные методы||
|Windows Server, версия 1809 |240 для поколения 2;<br>64 для поколения 1|Встроенные методы|| 
|Windows Server 2019 |240 для поколения 2;<br>64 для поколения 1|Встроенные методы||
|Windows Server версии 1803 |240 для поколения 2;<br>64 для поколения 1|Встроенные методы|| 
|Windows Server 2016 |240 для поколения 2;<br>64 для поколения 1|Встроенные методы|| 
|Windows Server 2012 R2 |64|Встроенные методы||  
|Windows Server 2012 |64|Встроенные методы||  
|Windows Server 2008 R2 с пакетом обновления 1 (SP1)|64|Установите все критические обновления Windows после настройки операционной системы на виртуальной машине.|Выпуски Datacenter, Enterprise, Standard и Web.|
|Windows Server 2008 с пакетом обновления 2 (SP2)|8|Установите все критические обновления Windows после настройки операционной системы на виртуальной машине.|Выпуски Datacenter, Enterprise, Standard и Web (32-разрядные и 64-разрядные).|  
  
## <a name="supported-windows-client-guest-operating-systems"></a>Поддерживаемые гостевые операционные системы клиента Windows  

Ниже приведены версии клиента Windows, которые поддерживаются в качестве гостевых операционных систем для Hyper-V в Windows Server 2016 и Windows Server 2019.
  
|Операционная система на виртуальной машине (клиент)|Максимальное число виртуальных процессоров.|Службы интеграции|Примечания|  
|-------------------------------------|----------------------------------------|------------------------|---------|  
|Windows 10|32|Встроенные методы||  
|Windows 8.1|32|Встроенные методы||  
|Windows 7 с пакетом обновления 1 (SP1)|4|Обновите службы Integration Services после настройки операционной системы на виртуальной машине.|Выпуски Максимальная, Корпоративная и Профессиональная (32-разрядные и 64-разрядные).|  
  
## <a name="guest-operating-system-support-on-other-versions-of-windows"></a>Поддержка гостевых операционных систем в других версиях Windows  

В следующей таблице приведены ссылки на сведения о гостевых операционных системах, поддерживаемых Hyper-V, в других версиях Windows.  
  
|Главная операционная система|Раздел|  
|-------------------------|---------|  
|Windows 10|[Поддерживаемые гостевые операционные системы для клиента Hyper-V в Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/about/supported-guest-os)|  
|Windows Server 2012 R2 и Windows 8.1|-   [Поддерживаемые гостевые операционные системы Windows для Hyper-V в Windows Server 2012 R2 и Windows 8.1](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn792027(v=ws.11))<br />-   [виртуальных машин Linux и FreeBSD в Hyper-V](Supported-Linux-and-FreeBSD-virtual-machines-for-Hyper-V-on-Windows.md)|  
|Windows Server 2012 и Windows 8|[Поддерживаемые гостевые операционные системы Windows для Hyper-V в Windows Server 2012 и Windows 8](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn792028(v=ws.11))|  
|Windows Server 2008 и Windows Server 2008 R2|[О виртуальных машинах и гостевых операционных системах](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc794868(v=ws.10))|  
  
## <a name="how-microsoft-provides-support-for-guest-operating-systems"></a>Как корпорация Майкрософт обеспечивает поддержку гостевых операционных систем  

Корпорация Майкрософт обеспечивает поддержку гостевых операционных систем следующим образом:  
  
-   Устранение проблем, обнаруженных в операционных системах Майкрософт и в службах интеграции, поддерживается службой технической поддержки Майкрософт.  
  
-   Поддержка по проблемам в других операционных системах, сертифицированных поставщиком операционной системы для выполнения в Hyper-V, обеспечивается поставщиком.  
  
-   Если обнаруживаются проблемы в других операционных системах, корпорация Майкрософт отправляет описание проблемы в сообщество по оказанию поддержки, состоящее из множества поставщиков, [TSANet](https://www.tsanet.org/).  
  
## <a name="see-also"></a>См. также:  
  
-   [Supported Linux and FreeBSD virtual machines for Hyper-V on Windows](Supported-Linux-and-FreeBSD-virtual-machines-for-Hyper-V-on-Windows.md) (Поддерживаемые виртуальные машины Linux и FreeBSD для Hyper-V в Windos).  
  
-   [Поддерживаемые гостевые операционные системы для клиента Hyper-V в Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/about/supported-guest-os)  
  



