---
title: Тестирование работы пользователей
description: Описывает способ использования Windows Server Essentials
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
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59838695"
---
# <a name="testing-the-customer-experience"></a>Тестирование работы пользователей

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Чтобы убедиться в удобстве работы пользователей и проверить настройки, сделанные вашим партнером, можно выполнить задачи начальной настройки на целевом компьютере. Рекомендуется хотя бы один раз выполнить начальную настройку вручную, чтобы повторить каждое действие пользователя. Если на панель администрирования добавляется совместная фирменная символика, необходимо выполнить начальную настройку для проверки отображения этой символики. Если администрирования сайта удаленного веб-доступа, вы должны получить доступ к http://<servername\> для проверки фирменную символику (< servername\> — это имя сервера). Для автоматизации тестирования действий пользователя во время начальной настройки можно использовать раздел Initial Configuration файла cfg.ini. Дополнительные сведения о создании данного раздела в файле cfg.ini см. в статье [Создание файла Cfg.ini](Create-the-Cfg.ini-File.md).  
  
> [!IMPORTANT]
>  Перед началом тестирования действий пользователя во время начальной настройки необходимо подготовить образ для развертывания с помощью средства командной строки Sysprep.exe. Дополнительные сведения о выполнении Sysprep.exe см. в статье [Preparing the Image for Deployment](Preparing-the-Image-for-Deployment.md).  
  
> [!IMPORTANT]
>  Для тестирования начальной настройки требуется подключение к сети. Не следует устанавливать или настраивать протокол DHCP на сервере — это позволит выполнить тестирование сети без помех.  
  
 Чтобы проверить сведения о поддержке, предоставляемой партнером, на панели администрирования щелкните стрелку рядом с кнопкой "Справка".  
  
## <a name="see-also"></a>См. также  
 [Создание и настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md)