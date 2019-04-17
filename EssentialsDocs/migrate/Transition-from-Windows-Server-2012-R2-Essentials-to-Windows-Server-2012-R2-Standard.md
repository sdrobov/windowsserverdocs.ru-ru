---
title: "Переход с Windows Server Essentials на Windows Server 2012 R2 Standard"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a14689e3-2310-4229-bd3e-dafc0e739e02
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: d371e24b17310c0687666185f56fe07a135ff91f
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="transition-from-windows-server-essentials-to-windows-server-2012-r2-standard"></a>Переход с Windows Server Essentials на Windows Server 2012 R2 Standard

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Windows Server 2016 используется облаке операционной системы, поддерживающий рабочих нагрузок в текущей, а также представляет новые технологии, которые упрощают переход на облачные вычисления. Windows Server 2016 содержимого помогает вам подготовиться.

 Windows Server Essentials поддерживает до 25 пользователей и 50 устройств. Если для потребностей вашего бизнеса ограничение, можно выполнить перенос лицензии на месте с Windows Server Essentials на Windows Server 2012 R2 Standard чтобы сохранить соответствие лицензии.  
  
 После перехода на Windows Server 2012 R2 Standard, удалены ограничения учетную запись и устройства пользователя, но функции, которые являются уникальными для Windows Server Essentials (например, панели мониторинга, удаленный веб-доступ и архивация данных клиентских компьютеров) по-прежнему остаются доступными. Тем не менее ограничений технического характера данные компоненты поддерживают не более 100 учетных записей и 200 устройств. Компонент архивации данных компьютера клиента будет поддерживать резервное копирование до 75 устройств.  
  
> [!IMPORTANT]
>   Windows Server 2012 R2 Standard требуется клиентской лицензии (CAL) для каждого пользователя или устройства в вашей среде. Это отличается от Windows Server Essentials, которая не используется модель клиентских лицензий и не предоставляются клиентские лицензии. Во время перехода с Windows Server Essentials на Windows Server 2012 R2 Standard, необходимо будет приобрести нужное количество клиентских лицензий подходящего типа для среды (в большинстве случаев приобретаются клиентские лицензии пользователя).  
  
## <a name="before-the-transition"></a>Перед переходом  
  
-   Перед переходом с Windows Server Essentials на Windows Server 2012 R2 Standard, следует создать полную резервную копию данных сервера.  
  
    > [!IMPORTANT]
    >  Без полной резервной копии сервера сервера нельзя восстановить состояние, в котором он находился до перехода.  
  
-   Кроме того убедитесь, что, чтение и понимание конечного пользователя условия лицензионного соглашения (EULA) для Windows Server 2012 R2 Standard. Чтобы просмотреть лицензионное соглашение:  
  
    1.  Откройте окно командной строки от имени администратора.  
  
    2.  Выполните следующую команду:  
  
         **DISM /online "" /set-edition: serverstandard / /geteula:***путь к лицензионному соглашению* (где *путь к лицензионному соглашению* представляет путь сохранения для файла EULA; например: C:\ws8std_eula.rtf). Обязательно укажите расширение файла RTF.  
  
    3.  Откройте папку, где сохранен файл и дважды щелкните файл, чтобы открыть его.  
  
## <a name="transition-to--windows-server-2012-r2-standard"></a>Переход на Windows Server 2012 R2 Standard  
 После того, как вы решили переход с Windows Server Essentials в Windows Server 2012 R2 Standard, полный в два этапа:  
  
1.  Приобрести лицензию для Windows Server 2012 R2 Standard и соответствующее количество пользователей и/или устройств клиентских лицензий для вашей среды.  
  
     Вы можете приобрести лицензию для Windows Server 2012 R2 Standard, в магазине, у дистрибьютора или с помощью [партнера Майкрософт](https://pinpoint.microsoft.com/SelectCulture.aspx).  
  
    > [!NOTE]
    >  Если вы купили Windows Server 2012 R2 Standard изначально и затем вы использовали право установки одного из двух виртуальных экземпляров в качестве Windows Server Essentials, приобретать дополнительные не нужно.  
    >   
    >  Если вы приобрели Windows Server 2012 R2 Standard через канал корпоративного лицензирования, можно загрузить ISO-образ и ключ продукта для Windows Server 2012 R2 Standard с корпоративных лицензий (VLSC).  
    >   
    >  Если вы приобрели Windows Server 2012 R2 Standard приобретается по другим каналам, можно загрузить ISO-образ и ознакомительный ключ продукта для Windows Server Essentials из [центра оценки TechNet](https://technet.microsoft.com/evalcenter/jj659306.aspx). Выполнить переход, как описано в следующем шаге превратит пробную версию продукта полностью лицензированных и поддерживаемых продукта.  
  
2.  Откройте Windows PowerShell от имени администратора и затем выполните следующую команду:  
  
     **DISM /online "" /set-edition: serverstandard / /accepteula /productkey:***ключ продукта* (где *ключ продукта* — это ключ продукта устанавливаемой вами копии Windows Server 2012 R2 Standard).  
  
     Для завершения перехода сервер перезагрузится.  
  
 После перехода компоненты Windows Server Essentials останутся на сервере и поддержка до 100 пользователей и 200 устройств.  
  
## <a name="see-also"></a>См. также:  
  

-   [Миграция данных сервера в Windows Server Essentials](Migrate-Server-Data-to-Windows-Server-Essentials.md)

-   [Миграция данных сервера в Windows Server Essentials](../migrate/Migrate-Server-Data-to-Windows-Server-Essentials.md)

