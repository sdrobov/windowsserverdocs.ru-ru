---
title: "Переход с Windows Server Essentials на Windows Server 2012 Standard"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 51bcf124-c215-4e9d-9fa8-a90fa2c2fa22
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: d2005b72adede72b718fa5b49b93435f5fbac1bd
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="transition-from-windows-server-essentials-to-windows-server-2012-standard"></a>Переход с Windows Server Essentials на Windows Server 2012 Standard

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

 Windows Server® 2012 Essentials поддерживает до 25 пользователей и 50 устройств. Если для потребностей вашего бизнеса ограничение, можно выполнить перенос лицензии на месте с Windows Server Essentials на Windows Server 2012 Standard чтобы сохранить соответствие лицензии.  
  
## <a name="how-the-transition-affects-user-and-device-limits"></a>Ограничивает влияние перехода на пользователей и устройств  
 После перехода на Windows Server 2012 Standard удалены ограничения учетную запись и устройства пользователя, но функции, которые являются уникальными для Windows Server Essentials (например, панель мониторинга, удаленный веб-доступ и резервное копирование клиентских компьютеров), по-прежнему остаются доступными. Тем не менее ограничений технического характера данные компоненты поддерживают не более 75 учетных записей пользователей и 75 устройств. Если потребуется добавить более 75 учетных записей пользователей или устройств, следует выключить компоненты Windows Server Essentials и использовать Windows Server 2012 Standard основные инструменты для управления учетными записями пользователей и устройств.  
  
> [!IMPORTANT]
>   Windows Server 2012 Standard требует Client Access License (CAL) для каждого пользователя или устройства в вашей среде. Это отличается от Windows Server Essentials, которая не используется модель клиентских лицензий и не предоставляются клиентские лицензии.  Во время перехода с Windows Server Essentials на Windows Server 2012 Standard, необходимо будет приобрести нужное количество клиентских лицензий подходящего типа для среды (в большинстве случаев приобретаются клиентские лицензии пользователя).  
  
## <a name="before-the-transition"></a>Перед переходом  
  
-   Перед переходом с Windows Server Essentials на Windows Server 2012 Standard, следует создать полную резервную копию данных сервера.  
  
    > [!IMPORTANT]
    >  Без полной резервной копии сервера сервера нельзя восстановить состояние, в котором он находился до перехода.  
  
-   Кроме того убедитесь, что, чтение и понимание конечного пользователя условия лицензионного соглашения (EULA) для Windows Server 2012 Standard. Чтобы просмотреть лицензионное соглашение:  
  
    1.  Откройте окно командной строки от имени администратора.  
  
    2.  Выполните следующую команду:  
  
         **DISM /online "" /set-edition: serverstandard / /geteula: путь к лицензионному соглашению**  
  
         Где **путь к лицензионному соглашению** представляет собой путь сохранения файла лицензионного соглашения. Например, для C:\ws8std_eula.RTF.  Обязательно укажите расширение файла RTF.  
  
    3.  Откройте папку, где сохранен файл и дважды щелкните файл, чтобы открыть его.  
  
## <a name="transition-to--windows-server-2012-standard"></a>Переход на Windows Server 2012 Standard  
 После того, как вы решили переход из Windows Server Essentials в Windows Server 2012 Standard, полный в два этапа:  
  
1.  Приобрести лицензию для Windows Server 2012 Standard и соответствующее количество пользователей и/или устройств клиентских лицензий для вашей среды.  
  
     Вы можете приобрести лицензию для Windows Server 2012 Standard в розничном магазине, у дистрибьютора или с помощью [партнера Майкрософт](https://pinpoint.microsoft.com/SelectCulture.aspx).  
  
    > [!NOTE]
    >  Если вы купили Windows Server 2012 Standard изначально и затем вы использовали право установки одного из двух виртуальных экземпляров в качестве Windows Server Essentials, приобретать дополнительные не нужно.  
    >   
    >  Если вы приобрели Windows Server 2012 Standard через канал корпоративного лицензирования, можно загрузить ISO-образ и ключ продукта для Windows Server 2012 Standard из корпоративных лицензий (VLSC).  
    >   
    >  Если вы приобрели Windows Server 2012 Standard по другим каналам можно загрузить ISO-образ и ознакомительный ключ продукта для Windows Server Essentials из [центра оценки TechNet](https://technet.microsoft.com/evalcenter/jj659306.aspx). Выполнить переход, как описано в следующем шаге превратит пробную версию продукта полностью лицензированных и поддерживаемых продукта.  
  
2.  Откройте Windows PowerShell от имени администратора и затем выполните следующую команду.  
  
     **DISM /online "" /set-edition: serverstandard / /accepteula /productkey:***ключ продукта*  
  
     Где *ключ продукта* — это ключ продукта устанавливаемой вами копии Windows Server 2012 Standard.  
  
     Для завершения перехода сервер перезагрузится.  
  
 После перехода компоненты Windows Server Essentials останутся на сервере и поддержка до 75 пользователей и 75 устройств. Если любое из этих ограничений будет превышено, следует использовать Windows Server 2012 Standard основные инструменты для управления учетными записями пользователей и устройств.  
  
 Кроме того после перехода на Windows Server 2012 Standard, Windows Server Essentials компонентов мультимедиа больше недоступны. Это касается компонентов мультимедиа удаленного веб-доступа и параметров мультимедиа на информационной панели.  
  
## <a name="turn-off--windows-server-essentials-features"></a>Отключение функций Windows Server Essentials  
 Если вы больше не нужна панели мониторинга Windows Server Essentials и другие дополнительные компоненты для управления сервером, можно отключить и удалить их с вашего сервера.  
  
 **Отключить мастер компонентов Windows Server Essentials** поможет удалить компоненты. Он также удаляет с сервера файлы, созданные программным обеспечением сервера Windows Server Essentials.  Некоторые операции удаления выполняются сразу, а другие запускаются после перезагрузки сервера.  
  
 **Отключить мастер компонентов Windows Server Essentials** необходимо вручную удалить все надстройки, перед выполнением мастера. Чтобы просмотреть список установленных надстроек, откройте страницу приложения на информационной панели. Мастер отобразит предупреждение, если он обнаруживает установленных надстроек и вам будет предложено удалить их.  
  
 **Отключить мастер компонентов Windows Server Essentials** позволяет выбрать, нужно ли сохранить файлы резервных копий для клиентских компьютеров после выключения компонентов Windows Server Essentials.  
  
 Существует два способа запуска **отключить мастер компонентов Windows Server Essentials** из панели мониторинга:  
  
#### <a name="from-the-alert"></a>Из предупреждения  
  
1.  С помощью панели мониторинга откройте средство просмотра оповещений.  
  
2.  В списке «Упорядочить» выберите предупреждение, в котором сообщается о выключении компонентов Windows Server Essentials после перехода.  
  
3.  В диалоговом окне оповещения, щелкните **выключить компоненты Windows Server Essentials**.  
  
#### <a name="from-the-get-help-and-support-pane"></a>Из области центра справки и поддержки  
  
1.  На домашней странице, щелкните центр справки и поддержки.  
  
2.  Нажмите кнопку **отключить мастер компонентов Windows Server Essentials**.  
  
 Возможно, некоторые задачи, выполняемые **отключить мастер компонентов Windows Server Essentials** не будет успешно завершена. В некоторых случаях это может препятствовать информационной панели запуска. В этом случае можно запустить мастер вручную, выполнив следующий файл:  
  
 **%SystemDrive%\Program Files\Windows Server\Bin\TurnOffFeaturesWizard.exe**  
  
## <a name="see-also"></a>См. также:  
  

-   [Переход на Windows Server 2012 R2 Standard](Transition-from-Windows-Server-2012-R2-Essentials-to-Windows-Server-2012-R2-Standard.md)  
  
-   [Миграция данных сервера в Windows Server Essentials](Migrate-Server-Data-to-Windows-Server-Essentials.md)

-   [Переход на Windows Server 2012 R2 Standard](../migrate/Transition-from-Windows-Server-2012-R2-Essentials-to-Windows-Server-2012-R2-Standard.md)  
  
-   [Миграция данных сервера в Windows Server Essentials](../migrate/Migrate-Server-Data-to-Windows-Server-Essentials.md)

