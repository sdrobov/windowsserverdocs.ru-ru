---
title: "Тестирование работы пользователей"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1b1a2040-4cfd-48bf-8d04-3ffde9c26b9b
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 223b0e1be3a53e9a7d198dc005fc8725e421db58
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="testing-the-customer-experience"></a>Тестирование работы пользователей

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Чтобы убедиться в удобстве работы пользователей и проверить настройки партнеров, выполните задачи начальной настройки на целевом компьютере. Рекомендуется выполнить начальную настройку хотя бы один раз вручную помогут разобраться в процессе работы пользователей. Если вы добавили панель мониторинга необходимо выполнить начальную настройку, чтобы проверить символику. Если вы добавили сайта удаленного веб-доступа, необходимо получить доступ к http://<servername\> для проверки отображения этой символики (имя_сервера < кземпляр > — это имя сервера). Раздел начальной настройки файла cfg.ini можно использовать для автоматизации тестирования действий пользователя. Дополнительные сведения о создании данного раздела в файле cfg.ini см [Создание файла Cfg.ini](Create-the-Cfg.ini-File.md).  
  
> [!IMPORTANT]
>  Необходимо выполнить команду Sysprep.exe для подготовки образа к развертыванию, перед запуском начальной настройки. Дополнительные сведения о выполнении Sysprep.exe см. в разделе [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md).  
  
> [!IMPORTANT]
>  Для тестирования начальной настройки требуется сетевое подключение. DHCP не настроено или не установлена на сервере, который позволяет тестирование сети без помех.  
  
 Чтобы проверить сведения для поддержки партнеров на информационной панели, нажмите стрелку вниз рядом с кнопкой справки.  
  
## <a name="see-also"></a>См. также:  
 [Создание и настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md)