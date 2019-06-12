---
title: Подготовка к установке Windows Server Essentials
description: Описывает способ использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8d0893bd-e2b7-4494-9537-02b1cbbcd57a
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 32b2b37e0d0109b8ad2a991b9f7693139103734d
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66433710"
---
# <a name="before-you-install-windows-server-essentials"></a>Подготовка к установке Windows Server Essentials

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

##  <a name="BKMK_BeforeYouBegin"></a> Прежде чем приступить к установке Windows Server Essentials, выполните следующие задачи.  

-   **Убедитесь, что компьютер соответствует минимальным требованиям к оборудованию**. Сюда входит определение того, если требуется дополнительное оборудование и проверка того, что драйверы для оборудования поддерживаются Windows Server Essentials. Дополнительные сведения см. в разделе [системных требований для Windows Server Essentials](../get-started/system-requirements.md).   


~~~
> [!IMPORTANT]
>  Before you install  Windows Server Essentials on a pre-existing computer, we recommend that you fully format and then repartition the hard disks of the pre-existing computer. By formatting and repartitioning the hard disks, you remove the possibility that hidden partitions remain on the hard disks.  
~~~

- **Подготовьте свою сеть** Чтобы подготовить сеть к установке Windows Server Essentials, выполните следующие действия:  


  - **Обновление операционной системы на клиентских компьютерах** Windows Server Essentials поддерживает следующие операционные системы:  Windows 8, Windows 7, Windows 10 и Macintosh OS X Lion или более поздней версии. В этих операционных системах присутствуют все необходимые средства безопасности, они обеспечивают надежность, производительность и функциональность для локальной сети.  

  - **Настройте маршрутизатор** Проверьте правильность настройки маршрутизатора.  

    -   На маршрутизаторе должна быть активна UPnP-инфраструктура.  

    -   Служба сервера DHCP для локальной сети может быть подключена или отключена.  Windows Server Essentials гарантирует, что DHCP не запущена на сервере и маршрутизаторе? Когда DHCP включен на маршрутизаторе, он отключен на сервере во время установки.  

    -   Ваш поставщик услуг Интернета (ISP) должен предоставить вам IP-адрес для внешнего интерфейса маршрутизатора. IP-адрес может либо динамически присваиваться службой сервера DHCP вашего ISP, либо вам необходимо вручную вводить статический IP-адрес с помощью консоли управления маршрутизатором.  

    -   Если ваше подключение к Интернету требует ввода имени пользователя и пароля (протокол точка-точка по Ethernet (PPPoE)), эти параметры должны быть настроены на маршрутизаторе, даже если устройство поддерживает инфраструктуру UPnP.  

    -   Маршрутизатор должен быть подключен к локальной сети и Интернету, он должен быть включен и нормально функционировать.  

    Если ваш маршрутизатор не поддерживает инфраструктуру UPnP, либо если его он не настраивается во время установки, необходимо вручную настроить его параметры в соответствии с вашей сетью. Убедитесь, что следующие порты открыты и настроены на IP-адрес конечного сервера:  

  |Номер порта|Приложение|  
  |-----------------|-----------------|  
  |Порт 80|Веб-трафик HTTP|  
  |Порт 443|Веб-трафик HTTPS|  


- **Чтение документация к выпуску Windows Server Essentials**. Документация к выпуску содержатся актуальные сведения, которые могут быть важны для правильной установки и настройки Windows Server Essentials. Чтобы просмотреть или распечатать документы к версии, см. в разделе [Release Documentation for Windows Server Essentials](../get-started/release-notes.md).  

## <a name="see-also"></a>См. также  

-   [Установка Windows Server Essentials](Install-Windows-Server-Essentials.md)

