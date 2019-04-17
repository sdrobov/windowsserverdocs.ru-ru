---
title: "Миграция с предыдущих версий на Windows Server Essentials или Windows Server Essentials Experience"
description: "Описывается, как использовать Windows Server Essentials"
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
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="migrate-from-previous-versions-to-windows-server-essentials-or-windows-server-essentials-experience"></a>Миграция с предыдущих версий на Windows Server Essentials или Windows Server Essentials Experience

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

В этом руководстве описывается Миграция с предыдущих версий Windows Small Business Server и Windows Server Essentials (включая Windows Server Essentials, Windows Small Business Server 2011 Standard, Windows Small Business Server 2011 Essentials, Windows Small Business Server 2008 и Windows Small Business Server 2003) для Windows Server Essentials или Windows Server 2012 R2, с установленной ролью Windows Server Essentials Experience.  
  
 **Для среды максимум с 25 пользователями и 50 устройств**, описанных в данном руководстве для миграции Windows Server Essentials из предыдущих версий Windows SBS.  
  
 **Для среды максимум с 100 пользователями и 200 устройств**, нужно выполнить те же правила для миграции на выпуски Standard или Datacenter Edition, Windows Server 2012 R2 с установленной ролью Windows Server Essentials Experience.  
  
> [!NOTE]
>  Во избежание проблем во время миграции, группа разработки продукта Windows Server Essentials настоятельно рекомендует, чтобы ознакомиться с этим документом перед началом миграции.  
  
## <a name="terms-and-definitions"></a>Термины и определения  
 **Исходный сервер** существующего сервера, с которого выполняется миграция параметров и данных.  
  
 **Конечный сервер** новый сервер, на котором выполняется миграция параметров и данных.  
  
## <a name="migration-process-summary"></a>Сводка по процессу миграции  
 Это руководство по миграции включает следующие этапы:  
  
1.  [Шаг 1: Подготовка к миграции исходного сервера для Windows Server Essentials](Step-1--Prepare-your-Source-Server-for-Windows-Server-Essentials-migration.md).  Необходимо убедиться, что исходный сервер и сеть готовы к миграции. Этот раздел помогает выполнить резервное копирование исходного сервера, проверка работоспособности его системы исходного сервера, установка последних пакетов обновления и исправления и проверка конфигурации сети.  
  
2.  [Шаг 2: Установка Windows Server Essentials в качестве нового репликата контроллера домена](Step-2--Install-Windows-Server-Essentials-as-a-new-replica-domain-controller.md). В этом разделе описывается установка Windows Server Essentials или Windows Server 2012 R2 Standard (с включенной ролью Windows Server Essentials Experience) как контроллер домена.  
  
3.  [Шаг 3: Присоединение компьютеров к новому серверу Windows Server Essentials](Step-3--Join-computers-to-the-new-Windows-Server-Essentials-server.md).  В этом разделе описывается процесс присоединения клиентских компьютеров к новому серверу под управлением Windows Server Essentials и обновления параметров групповой политики.  
  
4.  [Шаг 4: Перенос параметров и данных на целевой сервер для миграции Windows Server Essentials](Step-4--Move-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md).  Этот раздел содержит сведения о переносе данных и параметров с исходного сервера.  
  
5.  [Шаг 5: Включение перенаправления папок на конечный сервер для миграции Windows Server Essentials](Step-5--Enable-folder-redirection-on-the-Destination-Server-for-Windows-Server-Essentials-migration.md).  Если на исходном сервере включено перенаправление папок, можно включить перенаправление папок на конечном сервере и затем удалите старый параметр групповой политики перенаправления папок.  
  
6.  [Шаг 6: Понижение уровня и удаление исходного сервера из новой сети Windows Server Essentials](Step-6--Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md).  Перед удалением исходного сервера от сети, необходимо принудительное обновление групповой политики и понижение уровня исходного сервера.  
  
7.  [Шаг 7: Выполнение задач после миграции для миграции Windows Server Essentials](Step-7--Perform-post-migration-tasks-for-the-Windows-Server-Essentials-migration.md).  Завершив миграцию всех параметров и данных на Windows Server Essentials, можно сопоставить разрешенные компьютеры с учетными записями пользователей.  
  
8.  [Шаг 8: Запуск Windows Server Essentials Best Practices Analyzer](Step-8--Run-the-Windows-Server-Essentials-Best-Practices-Analyzer.md).  После завершения миграции параметров и данных на Windows Server Essentials, необходимо запустить Windows Server Essentials (Анализатор рекомендациям).  
  
 Для выполнения некоторых процедур миграции нужно открыть окно командной строки от имени администратора. Ниже описано, как это сделать.  
  
###  <a name="BKMK_OpenACommandPromptAsAdmin"></a>Чтобы открыть окно командной строки на исходном сервере от имени администратора  
  
1.  Нажмите кнопку **запустить**.  
  
2.  В поле поиска введите **cmd**.  
  
3.  В списке результатов щелкните правой кнопкой мыши **cmd**, а затем нажмите кнопку **Запуск от имени администратора**.  
  
#### <a name="to-open-a-command-prompt-window-on-the-destination-server-as-an-administrator"></a>Чтобы открыть окно командной строки на целевом сервере от имени администратора  
  
1.  На **запустить** экрана, в поле поиска введите **cmd**.  
  
2.  В списке результатов щелкните правой кнопкой мыши **cmd**, а затем нажмите кнопку **Запуск от имени администратора**.  
  
## <a name="see-also"></a>См. также:  
  
-   [Миграция данных сервера в Windows Server Essentials](Migrate-Server-Data-to-Windows-Server-Essentials.md)

-   [Миграция данных сервера в Windows Server Essentials](../migrate/Migrate-Server-Data-to-Windows-Server-Essentials.md)

