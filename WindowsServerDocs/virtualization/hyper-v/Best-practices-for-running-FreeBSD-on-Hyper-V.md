---
title: Рекомендации по использованию FreeBSD на Hyper-V
description: Рекомендации по использованию FreeBSD на виртуальных машинах
ms.prod: windows-server-threshold
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0c66f1c8-2606-43a3-b4cc-166acaaf2d2a
author: shirgall
ms.author: kathydav
ms.date: 01/09/2017
ms.openlocfilehash: 1a8efb4a991169258d6a11999513ce97d98130eb
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59816955"
---
# <a name="best-practices-for-running-freebsd-on-hyper-v"></a>Рекомендации по использованию FreeBSD на Hyper-V

>Область применения. Windows Server 2016, Hyper-V Server 2016, Windows Server 2012 R2, Hyper-V Server 2012 R2, Windows Server 2012, Hyper-V Server 2012, Windows Server 2008 R2, Windows 10, Windows 8.1, Windows 8, Windows 7.1, Windows 7

В этом разделе содержится список рекомендаций по использованию FreeBSD в качестве гостевой операционной системы на виртуальной машине Hyper-V.

## <a name="enable-carp-in-freebsd-102-on-hyper-v"></a>Включить CARP в FreeBSD 10.2 на Hyper-V

Протокол избыточности общие адрес (CARP) позволяет нескольким узлам совместно использовать один и тот же адрес IP-адрес и идентификатор виртуального узла (VHID) для обеспечения высокого уровня доступности для одной или нескольких служб. Если не один или несколько узлов, другие узлы прозрачно себя, пользователи не заметят сбоя службы. Чтобы использовать CARP в FreeBSD 10.2, следуйте инструкциям в [руководстве FreeBSD](https://www.freebsd.org/doc/en/books/handbook/carp.html) и выполните следующие действия в диспетчере Hyper-V.

* Проверьте у сетевого адаптера виртуальной машины и ей назначено виртуальному коммутатору. Выберите виртуальную машину и выберите **действия** > **параметры**.

![Снимок экрана: параметры виртуальной машины с выбранный сетевой адаптер](media/Hyper-V_Settings_NetworkAdapter.png)

* Включите спуфинг MAC-адресов. Чтобы сделать это,

   1. Выберите виртуальную машину и выберите **действия** > **параметры**.

   2. Разверните **сетевой адаптер** и выберите **дополнительные функции**.

   3. Выберите **спуфинг MAC-адрес включить**.

## <a name="create-labels-for-disk-devices"></a>Создание меток для дисковых устройств

Во время запуска узлы устройства создаются при обнаружении новых устройств. Это может означать, что имена устройств можно изменить, когда добавляются новые устройства. Если вы получите ошибку подключения КОРНЕВОГО во время запуска, следует создать метки для каждой секции интегрированной среды разработки, чтобы избежать конфликтов и изменений. Чтобы узнать как это сделать, см. в разделе [меток дисковых устройств](https://www.freebsd.org/doc/handbook/geom-glabel.html). Ниже приведены примеры. 

> [!IMPORTANT]
> Создайте резервную копию вашего fstab перед внесением любых изменений.

1. Перезагрузите систему в однопользовательском режиме. Это можно сделать, выбрав параметр меню загрузки 2 для FreeBSD 10.3 (вариант 4 для FreeBSD 8.x), или выполнение «загрузки -s» в командной строке загрузки.

2. В однопользовательском режиме создайте GEOM метки для каждого из разделов диска интегрированной среды разработки, перечисленных в вашей fstab (root и подкачки). Ниже приведен пример FreeBSD 10.3.

   ```bash
   # cat  /etc/fstab
   # Device           Mountpoint      FStype  Options   Dump   Pass#
   /dev/da0p2         /               ufs     rw        1       1
   /dev/da0p3         none            swap    sw        0       0

   # glabel  label rootfs  /dev/da0p2
   # glabel  label swap   /dev/da0p3
   # exit
   ```

   Дополнительные сведения о GEOM метки можно найти в: [Добавление меток дисковых устройств](https://www.freebsd.org/doc/handbook/geom-glabel.html).

3. Система будет продолжена с загрузки нескольких пользователей. После завершения загрузки, изменить/etc/fstab и заменить имена стандартных устройств, их соответствующие метки. Окончательный/etc/fstab будет выглядеть следующим образом:

   ```
   # Device                Mountpoint      FStype  Options         Dump    Pass#
   /dev/label/rootfs       /               ufs     rw              1       1
   /dev/label/swap         none            swap    sw              0       0

   ```

4.  Теперь можно выполнить перезагрузку системы. Если все пройдет успешно, он будет нормально и подключения будет отображаться:
   
   ```
   # mount
   /dev/label/rootfs on / (ufs, local, journaled soft-updates)
   devfs on /dev (devfs, local, mutilabel)
   ```

## <a name="use-a-wireless-network-adapter-as-the-virtual-switch"></a>Использовать адаптер беспроводной сети в качестве виртуального коммутатора

Если виртуальный коммутатор на узле основана на адаптер беспроводной сети, сократить время истечения срока действия ARP в 60 секунд, с помощью следующей команды. В противном случае подключение к сети виртуальной Машины может перестать работать через некоторое время.


```
   # sysctl net.link.ether.inet.max_age=60
```


См. также

* [Поддерживаемые виртуальные машины FreeBSD в Hyper-V](Supported-FreeBSD-virtual-machines-on-Hyper-V.md)
