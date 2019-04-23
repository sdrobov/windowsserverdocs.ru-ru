---
title: Переход с Windows Server Essentials на Windows Server 2012 Standard
description: Описывает способ использования Windows Server Essentials
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
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59882505"
---
# <a name="transition-from-windows-server-essentials-to-windows-server-2012-standard"></a>Переход с Windows Server Essentials на Windows Server 2012 Standard

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

 Windows Server® 2012 Essentials поддерживает до 25 пользователей и 50 устройств. Если недостаточно для потребностей вашего бизнеса, можно выполнить перенос лицензии на месте с Windows Server Essentials для Windows Server 2012 Standard чтобы сохранить приобретенную лицензию.  
  
## <a name="how-the-transition-affects-user-and-device-limits"></a>Влияние перехода на предельное число пользователей и устройств  
 После перехода на Windows Server 2012 Standard, пределы учетной записи и устройства пользователей будут удалены, но функции, которые уникальны для Windows Server Essentials (например, панель мониторинга, удаленного веб-доступа и резервное копирование клиентских компьютеров), по-прежнему остаются доступными. Из-за технических особенностей данные компоненты поддерживают не более 75 учетных записей и 75 устройств. Если потребуется добавить более 75 учетных записей пользователей или устройств, необходимо выключить компоненты Windows Server Essentials и использовать Windows Server 2012 Standard собственных средств для управления учетными записями пользователей и устройств.  
  
> [!IMPORTANT]
>   Windows Server 2012 Standard требуется клиентскую лицензию (CAL) для каждого пользователя или устройства в вашей среде. Это отличается от Windows Server Essentials, которая не использует модель клиентских лицензий и не предоставляются клиентские лицензии.  Во время перехода с Windows Server Essentials для Windows Server 2012 Standard, необходимо будет приобрести нужное количество клиентских лицензий подходящего типа для вашей среды (в большинстве случаев приобретаются клиентские лицензии пользователя).  
  
## <a name="before-the-transition"></a>Перед переходом  
  
-   Перед переходом с Windows Server Essentials для Windows Server 2012 Standard, следует создавать резервные копии данных на сервере.  
  
    > [!IMPORTANT]
    >  Без полной резервной копии сервера будет невозможно восстановить состояние сервера до перехода.  
  
-   Кроме того убедитесь, что, прочитать и понять лицензионного соглашения конечного пользователя (EULA) для Windows Server 2012 Standard. Чтобы просмотреть лицензионное соглашение, выполните следующие действия.  
  
    1.  Откройте окно командной строки от имени администратора.  
  
    2.  Выполните следующую команду:  
  
         **DISM / online/set-edition: serverstandard / geteula: путь eula**  
  
         Здесь **путь eula** обозначает расположение для сохранения файла лицензионного соглашения. Пример: C:\ws8std_eula.rtf.  Обязательно укажите в качестве расширения имени файла ".rtf".  
  
    3.  Откройте папку, в которой сохранен файл, и дважды щелкните его, чтобы открыть.  
  
## <a name="transition-to--windows-server-2012-standard"></a>Переход на Windows Server 2012 Standard  
 После того, как вы решили переход из Windows Server Essentials в Windows Server 2012 Standard, полный следующие два действия:  
  
1.  Приобретите лицензию на Windows Server 2012 Standard и соответствующее количество пользователей и/или устройств клиентские лицензии для вашей среды.  
  
     Вы можете приобрести лицензии для Windows Server 2012 Standard, у дистрибьютора,, или с помощью [Microsoft Partner](https://pinpoint.microsoft.com/SelectCulture.aspx).  
  
    > [!NOTE]
    >  Если вы приобрели по Windows Server 2012 Standard изначально и охвачены право установки одного из двух виртуальных экземпляров как Windows Server Essentials, вы не обязательно должны приобрести дополнительные компоненты или действия.  
    >   
    >  При покупке по Windows Server 2012 Standard через канал корпоративного лицензирования, можно загрузить ISO-образ и ключ продукта для Windows Server 2012 Standard из Volume Licensing Service Center (VLSC).  
    >   
    >  При приобретении Windows Server 2012 Standard из других каналов можно загрузить ISO-образ и ознакомительный ключ продукта для Windows Server Essentials из [центра оценки TechNet](https://technet.microsoft.com/evalcenter/jj659306.aspx). Далее описано, как выполнить переход, чтобы преобразовать пробную версию продукта в полную лицензионную версию, обеспечиваемую поддержкой.  
  
2.  Откройте Windows PowerShell от имени администратора и выполните следующую команду:  
  
     **DISM / online/set-edition: ServerStandard/ACCEPTEULA/ProductKey:** *Ключ продукта*  
  
     Где *ключ продукта* — ключ продукта устанавливаемой копии Windows Server 2012 Standard.  
  
     Для завершения перехода сервер перезагрузится.  
  
 После перехода компоненты Windows Server Essentials на сервере и поддержка до 75 пользователей и 75 устройств. Если любое из этих ограничений превышено, следует использовать Windows Server 2012 Standard собственных средств для управления учетными записями пользователей и устройств.  
  
 Кроме того после перехода на Windows Server 2012 Standard, возможности работы с мультимедиа Windows Server Essentials, больше не доступны. Это касается компонентов мультимедиа удаленного веб-доступа и параметров мультимедиа на информационной панели.  
  
## <a name="turn-off--windows-server-essentials-features"></a>Выключить компоненты Windows Server Essentials  
 Если вы больше не нужны, панели мониторинга Windows Server Essentials и другие дополнительные компоненты для управления сервером, можно отключить и удалить их с сервера.  
  
 **Windows Server Essentials мастер выключения компонентов** поможет удалить компоненты. Он также удаляет с сервера файлы, которые были созданы серверное программное обеспечение Windows Server Essentials.  Некоторые операции удаления выполняются сразу, а другие запускаются после перезагрузки сервера.  
  
 **Windows Server Essentials мастер выключения компонентов** необходимо вручную удалить все надстройки, перед выполнением мастера. Чтобы просмотреть список установленных надстроек, откройте страницу "Приложение" на информационной панели. Если мастер обнаружит установленные надстройки, появится предупреждение с предложением удалить их.  
  
 **Windows Server Essentials мастер выключения компонентов** позволяет выбрать, следует ли сохранять файлы резервных копий для клиентских компьютеров после выключения компонентов Windows Server Essentials.  
  
 Существует два способа запуска **Windows Server Essentials мастер выключения компонентов** из панели мониторинга:  
  
#### <a name="from-the-alert"></a>Из предупреждения  
  
1.  Откройте представление "Предупреждения" на информационной панели.  
  
2.  В списке «Упорядочить» выберите оповещение, которое сообщает сведения об отключении функций Windows Server Essentials после перехода.  
  
3.  В диалоговом окне оповещения, щелкните **выключить компоненты Windows Server Essentials**.  
  
#### <a name="from-the-get-help-and-support-pane"></a>Из центра справки и поддержки  
  
1.  Щелкните ссылку "Центр справки и поддержки" на домашней странице.  
  
2.  Нажмите кнопку **Windows Server Essentials мастер выключения компонентов**.  
  
 Возможно, некоторые задачи, выполняемые **Windows Server Essentials мастер выключения компонентов** не будет успешно завершена. В некоторых случаях это может препятствовать запуску информационной панели. Тогда можно запустить мастер вручную, выполнив следующий файл:  
  
 **%SystemDrive%\Program Files\Windows Server\Bin\TurnOffFeaturesWizard.exe**  
  
## <a name="see-also"></a>См. также  
  

-   [Переход на Windows Server 2012 R2 Standard](Transition-from-Windows-Server-2012-R2-Essentials-to-Windows-Server-2012-R2-Standard.md)  
  
-   [Миграция данных сервера в Windows Server Essentials](Migrate-Server-Data-to-Windows-Server-Essentials.md)

-   [Переход на Windows Server 2012 R2 Standard](../migrate/Transition-from-Windows-Server-2012-R2-Essentials-to-Windows-Server-2012-R2-Standard.md)  
  
-   [Миграция данных сервера в Windows Server Essentials](../migrate/Migrate-Server-Data-to-Windows-Server-Essentials.md)

