---
title: Миграция с предыдущих версий на Windows Server Essentials или Windows Server Essentials Experience
description: Описывает способ использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/20116
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2974fb3a-5150-43fd-a73f-3e5074eb5d03
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 213ee4304d9d4ebdb7580f7f78fdaca78aa454c9
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59883875"
---
# <a name="migrate-from-previous-versions-to-windows-server-essentials-or-windows-server-essentials-experience"></a>Миграция с предыдущих версий на Windows Server Essentials или Windows Server Essentials Experience

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

В этом руководстве описывается Миграция с предыдущих версий Windows Small Business Server и Windows Server Essentials (включая Windows Server Essentials, Windows Small Business Server 2011 Standard, Windows Small Business Server 2011 Essentials, Windows Small Business Server 2008 и Windows Small Business Server 2003) на Windows Server Essentials или Windows Server 2012 R2 с установленной ролью Windows Server Essentials Experience.  
  
 **Для среды максимум с 25 пользователями и 50 устройствами**, необходимо выполнить действия, описанные в этом руководстве для миграции Windows Server Essentials из предыдущих версий Windows SBS.  
  
 **Для среды максимум с 100 пользователями и 200 устройств**, необходимо выполнить то же руководство для миграции на выпуски Standard или Datacenter, Windows Server 2012 R2 с установленной ролью Windows Server Essentials Experience.  
  
> [!NOTE]
>  Во избежание проблем во время миграции группа разработки продукта Windows Server Essentials настоятельно рекомендует ознакомиться с этим документом перед началом миграции.  
  
## <a name="terms-and-definitions"></a>Термины и определения  
 **Исходный сервер:** существующий сервер, с которого выполняется миграция параметров и данных.  
  
 **Целевой сервер:** новый сервер, на который выполняется миграция параметров и данных.  
  
## <a name="migration-process-summary"></a>Сводка по процессу миграции  
 Настоящее руководство по миграции состоит из следующих разделов:  
  
1.  [Шаг 1. Подготовка к миграции исходного сервера для Windows Server Essentials](Step-1--Prepare-your-Source-Server-for-Windows-Server-Essentials-migration.md).  Убедитесь, что исходный сервер и сеть готовы к миграции. В этом разделе подробно описаны архивация параметров исходного сервера, проверка работоспособности его системы, установка последних пакетов обновления и исправлений, а также проверка параметров сети.  
  
2.  [Шаг 2. Установка Windows Server Essentials в качестве нового репликата контроллера домена](Step-2--Install-Windows-Server-Essentials-as-a-new-replica-domain-controller.md). В этом разделе описывается установка Windows Server Essentials или Windows Server 2012 R2 Standard (с включенной ролью Windows Server Essentials Experience) как контроллер домена.  
  
3.  [Шаг 3. Присоединение компьютеров к новому серверу Windows Server Essentials](Step-3--Join-computers-to-the-new-Windows-Server-Essentials-server.md).  В этом разделе описывается процесс присоединения клиентских компьютеров к новому серверу под управлением Windows Server Essentials и обновления параметров групповой политики.  
  
4.  [Шаг 4. Перенос параметров и данных на целевой сервер для миграции Windows Server Essentials](Step-4--Move-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md).  Этот раздел содержит сведения о переносе данных и параметров с исходного сервера.  
  
5.  [Шаг 5. Включение перенаправления папок на конечный сервер для миграции Windows Server Essentials](Step-5--Enable-folder-redirection-on-the-Destination-Server-for-Windows-Server-Essentials-migration.md).  Если перенаправление папок включено на исходном сервере, его можно включить на конечном сервере и затем удалить старый параметр групповой политики "Перенаправление папок".  
  
6.  [Шаг 6. Понижение уровня и удаление исходного сервера из новой сети Windows Server Essentials](Step-6--Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md).  Прежде чем удалить исходный сервер из сети, необходимо принудительно обновить групповую политику и понизить уровень исходного сервера.  
  
7.  [Шаг 7. Выполнение задач после миграции для миграции Windows Server Essentials](Step-7--Perform-post-migration-tasks-for-the-Windows-Server-Essentials-migration.md).  Завершив миграцию всех параметров и данных на Windows Server Essentials, вы можете сопоставить разрешенные компьютеры с учетными записями пользователей.  
  
8.  [Шаг 8. Запустите Windows Server Essentials Best Practices Analyzer](Step-8--Run-the-Windows-Server-Essentials-Best-Practices-Analyzer.md).  После завершения миграции параметров и данных на Windows Server Essentials, необходимо запустить Windows Server Essentials рекомендации анализатор соответствия рекомендациям (BPA).  
  
 Для выполнения некоторых процедур миграции нужно открыть окно командной строки от имени администратора. Ниже описано, как это сделать.  
  
###  <a name="BKMK_OpenACommandPromptAsAdmin"></a> Чтобы открыть окно командной строки на исходном сервере с правами администратора  
  
1.  Щелкните **Пуск**.  
  
2.  В поле поиска введите **cmd**.  
  
3.  В списке результатов правой кнопкой мыши щелкните команду **cmd**и выберите пункт **Запуск от имени администратора**.  
  
#### <a name="to-open-a-command-prompt-window-on-the-destination-server-as-an-administrator"></a>Открытие окна командной строки на конечном сервере от имени администратора  
  
1.  На **начальном экране** в поле поиска введите **cmd**.  
  
2.  В списке результатов правой кнопкой мыши щелкните команду **cmd**и выберите пункт **Запуск от имени администратора**.  
  
## <a name="see-also"></a>См. также  
  
-   [Миграция данных сервера в Windows Server Essentials](Migrate-Server-Data-to-Windows-Server-Essentials.md)

-   [Миграция данных сервера в Windows Server Essentials](../migrate/Migrate-Server-Data-to-Windows-Server-Essentials.md)

