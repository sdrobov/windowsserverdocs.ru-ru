---
title: Настройка USB ноль станции клиент подключен в службах MultiPoint
description: Сведения о создании станции ноль клиента USB в службах MultiPoint
ms.custom: na
ms.date: 07/22/2016
ms.prod: windows-server-threshold
ms.technology: multipoint-services
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d2908865-6be3-474d-88f1-995f40bb61d0
author: lizap
manager: dongill
ms.author: elizapo
ms.openlocfilehash: 1a64373f4ed5e0d1ac96a0257ac5697ff94ffcbe
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59878935"
---
# <a name="set-up-a-usb-zero-client-connected-station-in-multipoint-services"></a>Настройка USB ноль станции клиент подключен в службах MultiPoint
При использовании клиентов USB zero для создания станции MultiPoint Services, монитор для каждой станции подключается к видеопорту клиент USB zero, как показано на следующем рисунке. Дополнительные сведения об этом и других типов станции см. в разделе [станции MultiPoint](MultiPoint-services-Stations.md).
  
**Система multiPoint Services с одной рабочей станции на подключенных напрямую видео и две станции USB zero клиент подключен**  
  
![Станции USB zero client](./media/WMS11_diagram7.gif)  
  
> [!IMPORTANT]  
> Перед настройкой USB ноль станций клиент подключен, не забудьте установить последние версии драйверов для вашей видеоадаптеров и клиент USB zero. Устаревшие драйверы может помешать успешному конфигурации MultiPoint Services. Инструкции см. в разделе [обновления и устанавливать драйверы устройств, при необходимости](Update-and-install-device-drivers-if-needed.md).  
  
> [!IMPORTANT]  
> Если вы используете клиент USB через Ethernet ноль, следуйте инструкциям от поставщика, вместо этой процедуры, в которых будет производиться Настройка устройства в сети Ethernet-подключение.  
  
### <a name="to-set-up-a-usb-zero-client-connected-station"></a>Чтобы настроить USB ноль станции клиент подключен  
  
1.  Подключения кабель видеомонитора к порту отображения видео DVI или VGA на USB ноль клиента, как показано на следующем рисунке.  
  
    ![Изображение видеоподключения к системе на основе USB-концентратора](./media/WMSVideoConnection.gif)  
  
2.  Подключите клиент USB zero к доступному порту USB компьютера.  
  
    ![Изображение подключения MultiPoint Services USB-концентратора](./media/WMSUSBHubConnection.gif)  
  
3.  Подключите клавиатуру и мышь клиенту USB zero.  
  
    ![Изображение входящих подключений устройств к USB-концентратору](./media/WMSUSBDeviceConnection.gif)  
  
4.  Если вы используете клиент USB zero внешним питанием, подключите шнур питания USB zero клиента к розетке питания.  
  
5.  Подключите шнур питания видеомонитора к розетке питания.  
  
6.  Если будет предложено связать устройства с помощью станции, следуйте инструкциям на мониторе, чтобы завершить настройку. (Как правило, USB ноль станций клиент подключен связаны с станции автоматически по мере их добавления на сервер.)