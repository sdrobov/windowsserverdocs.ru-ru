---
title: Переход с Windows Server Essentials на Windows Server 2012 R2 Standard
description: Описывает способ использования Windows Server Essentials
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
ms.openlocfilehash: ca36533af169c899865789f153960bf5f0dda684
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66432551"
---
# <a name="transition-from-windows-server-essentials-to-windows-server-2012-r2-standard"></a>Переход с Windows Server Essentials на Windows Server 2012 R2 Standard

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Windows Server 2016 — это готовое для облачной операционной системы, которая поддерживает все существующие рабочие нагрузки, одновременно предлагая новые технологии, которые упрощают переход к облачным вычислениям. Windows Server 2016 содержимого помогает готовим вас к установке.

 Windows Server Essentials поддерживает до 25 пользователей и 50 устройств. Если недостаточно для потребностей вашего бизнеса, можно выполнить перенос лицензии на месте с Windows Server Essentials на Windows Server 2012 R2 Standard чтобы сохранить приобретенную лицензию.  
  
 После перехода на Windows Server 2012 R2 Standard, пределы учетной записи и устройства пользователей будут удалены, но функции, которые уникальны для Windows Server Essentials (например, панель мониторинга, удаленного веб-доступа и резервное копирование клиентских компьютеров) по-прежнему остаются доступными. Из-за ограничений технического характера данные компоненты поддерживают не более 100 учетных записей и 200 устройств. Компонент архивации данных клиентского компьютера будет поддерживать резервное копирование данных с клиентских компьютеров количеством не более 75.  
  
> [!IMPORTANT]
>   Windows Server 2012 R2 Standard требуется клиентской лицензии (CAL) для каждого пользователя или устройства в вашей среде. Это отличается от Windows Server Essentials, которая не использует модель клиентских лицензий и не предоставляются клиентские лицензии. Во время перехода с Windows Server Essentials на Windows Server 2012 R2 Standard, необходимо будет приобрести нужное количество клиентских лицензий подходящего типа для вашей среды (в большинстве случаев приобретаются клиентские лицензии пользователя).  
  
## <a name="before-the-transition"></a>Перед переходом  
  
-   Перед переходом с Windows Server Essentials на Windows Server 2012 R2 Standard, следует создавать резервные копии данных на сервере.  
  
    > [!IMPORTANT]
    >  Без полной резервной копии сервера будет невозможно восстановить состояние сервера до перехода.  
  
-   Кроме того убедитесь, что, прочитать и понять лицензионного соглашения конечного пользователя (EULA) для Windows Server 2012 R2 Standard. Чтобы просмотреть лицензионное соглашение, выполните следующие действия.  
  
    1.  Откройте окно командной строки от имени администратора.  
  
    2.  Выполните следующую команду:  
  
         **DISM / online/set-edition: serverstandard / geteula:** *путь eula* (где *путь eula* представляет расположение, к которому вы хотите сохранить для файла EULA; например: C:\ws8std_eula.rtf). Обязательно укажите в качестве расширения имени файла ".rtf".  
  
    3.  Откройте папку, в которой сохранен файл, и дважды щелкните его, чтобы открыть.  
  
## <a name="transition-to--windows-server-2012-r2-standard"></a>Переход на Windows Server 2012 R2 Standard  
 После того, как вы решили переход из Windows Server Essentials в Windows Server 2012 R2 Standard, полный следующие два действия:  
  
1. Приобретите лицензию на Windows Server 2012 R2 Standard и соответствующее количество пользователей и/или устройств клиентских лицензий для вашей среды.  
  
    Вы можете приобрести лицензии для Windows Server 2012 R2 Standard, у дистрибьютора,, или с помощью [Microsoft Partner](https://pinpoint.microsoft.com/SelectCulture.aspx).  
  
   > [!NOTE]
   >  Если вы изначально приобрести Windows Server 2012 R2 Standard и охвачены право установки одного из двух виртуальных экземпляров как Windows Server Essentials, вы не обязательно должны приобретать дополнительные.  
   >   
   >  При приобретении Windows Server 2012 R2 Standard, через канал корпоративного лицензирования, можно загрузить ISO-образ и ключ продукта для Windows Server 2012 R2 Standard с Volume Licensing Service Center (VLSC).  
   >   
   >  При приобретении Windows Server 2012 R2 Standard другим каналам, можно загрузить ISO-образ и ознакомительный ключ продукта для Windows Server Essentials из [центра оценки TechNet](https://technet.microsoft.com/evalcenter/jj659306.aspx). Далее описано, как выполнить переход, чтобы преобразовать пробную версию продукта в полную лицензионную версию, обеспечиваемую поддержкой.  
  
2. Откройте Windows PowerShell с правами администратора и выполните следующую команду:  
  
    **DISM / online/set-edition: ServerStandard/ACCEPTEULA/ProductKey:** *Ключ продукта* (где *ключ продукта* — ключ продукта устанавливаемой копии Windows Server 2012 R2 Standard).  
  
    Для завершения перехода сервер перезагрузится.  
  
   После перехода компоненты Windows Server Essentials на сервере и поддержка до 100 пользователей и 200 устройств.  
  
## <a name="see-also"></a>См. также  
  

-   [Перенос данных сервера в Windows Server Essentials](Migrate-Server-Data-to-Windows-Server-Essentials.md)

-   [Перенос данных сервера в Windows Server Essentials](../migrate/Migrate-Server-Data-to-Windows-Server-Essentials.md)

