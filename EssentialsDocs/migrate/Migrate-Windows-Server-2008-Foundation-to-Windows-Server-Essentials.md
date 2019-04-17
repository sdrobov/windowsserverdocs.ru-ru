---
title: "Миграция с Windows Server 2008 Foundation на Windows Server Essentials"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f22fc0a4-cb82-4e60-afe6-2d03145745e7
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 22721833d3ba97c7860c949764d565415bbc7cab
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="migrate-windows-server-2008-foundation-to-windows-server-essentials"></a>Миграция с Windows Server 2008 Foundation на Windows Server Essentials

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

В этом руководстве описывается, как выполнить миграцию существующего домена Windows Server 2008 Foundation на Windows Server® 2012 Essentials на новом оборудовании, а затем перенести параметры и данные. В этом руководстве также описывается удалить существующий сервер из сети Windows Server Essentials после завершения миграции.  
  
> [!NOTE]
>  Во избежание проблем во время миграции группа разработки продукта Windows Server Essentials настоятельно рекомендует читать этот документ, прежде чем приступить к переносу.  
  
## <a name="additional-resources"></a>Дополнительные ресурсы  
 Ссылки на дополнительные сведения, инструменты и ресурсы сообщества в помощь в процессе миграции см. в разделе [миграции Windows Small Business Server](https://go.microsoft.com/fwlink/?LinkId=217520).  
  
## <a name="terms-and-definitions"></a>Термины и определения  
 **Исходный сервер:** существующего сервера, с которого выполняется миграция параметров и данных.  
  
 **Конечный сервер:** новый сервер, на котором выполняется миграция параметров и данных.  
  
## <a name="migration-process-summary"></a>Сводка по процессу миграции  
 Это руководство по миграции включает следующие этапы:  
  

1.  [Подготовка к миграции исходного сервера для Windows Server Essentials](Prepare-your-Source-Server-for-Windows-Server-Essentials-migration.md).  Необходимо убедиться, что исходный сервер и сеть готовы к миграции. Этот раздел помогает выполнить резервное копирование исходного сервера, проверка работоспособности его системы исходного сервера, установка последних пакетов обновления и исправления и проверка конфигурации сети.  
  
2.  [Установка Windows Server Essentials в режиме миграции](Install-Windows-Server-Essentials-in-migration-mode.md).  В этом разделе описаны действия, которые необходимо выполнить для установки Windows Server Essentials на конечном сервере в режиме миграции.  
  
3.  [Присоединение компьютеров к новой сети Windows Server Essentials](Join-computers-to-the-new-Windows-Server-Essentials-network.md).  В этом разделе рассматриваются присоединении клиентских компьютеров к новой сети Windows Server Essentials и обновления параметров групповой политики.  
  
4.  [Перемещение данных и параметров в Windows Server 2008 Foundation на целевой сервер](Move-Windows-Server-2008-Foundation-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md).  Этот раздел содержит сведения о переносе данных и параметров с исходного сервера.  
  
5.  [Понижение уровня и удаление исходного сервера из новой сети Windows Server Essentials](Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md).  Перед удалением исходного сервера от сети, необходимо принудительное обновление групповой политики и понижение уровня исходного сервера.  
  
6.  [Выполнение задач после миграции для миграции Windows Server Essentials](Perform-post-migration-tasks-for-Windows-Server-Essentials-migration.md).  Завершив миграцию всех параметров и данных на Windows Server Essentials, можно сопоставить разрешенные компьютеры с учетными записями пользователей.  
  
7.  [Запустите Windows Server Essentials Best Practices Analyzer](Run-the-Windows-Server-Essentials-Best-Practices-Analyzer.md).  После завершения миграции параметров и данных на Windows Server Essentials, необходимо запустить анализатор соответствия Рекомендациям Windows Server Essentials.  

1.  [Подготовка к миграции исходного сервера для Windows Server Essentials](../migrate/Prepare-your-Source-Server-for-Windows-Server-Essentials-migration.md).  Необходимо убедиться, что исходный сервер и сеть готовы к миграции. Этот раздел помогает выполнить резервное копирование исходного сервера, проверка работоспособности его системы исходного сервера, установка последних пакетов обновления и исправления и проверка конфигурации сети.  
  
2.  [Установка Windows Server Essentials в режиме миграции](../migrate/Install-Windows-Server-Essentials-in-migration-mode.md).  В этом разделе описаны действия, которые необходимо выполнить для установки Windows Server Essentials на конечном сервере в режиме миграции.  
  
3.  [Присоединение компьютеров к новой сети Windows Server Essentials](../migrate/Join-computers-to-the-new-Windows-Server-Essentials-network.md).  В этом разделе рассматриваются присоединении клиентских компьютеров к новой сети Windows Server Essentials и обновления параметров групповой политики.  
  
4.  [Перемещение данных и параметров в Windows Server 2008 Foundation на целевой сервер](../migrate/Move-Windows-Server-2008-Foundation-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md).  Этот раздел содержит сведения о переносе данных и параметров с исходного сервера.  
  
5.  [Понижение уровня и удаление исходного сервера из новой сети Windows Server Essentials](../migrate/Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md).  Перед удалением исходного сервера от сети, необходимо принудительное обновление групповой политики и понижение уровня исходного сервера.  
  
6.  [Выполнение задач после миграции для миграции Windows Server Essentials](../migrate/Perform-post-migration-tasks-for-Windows-Server-Essentials-migration.md).  Завершив миграцию всех параметров и данных на Windows Server Essentials, можно сопоставить разрешенные компьютеры с учетными записями пользователей.  
  
7.  [Запустите Windows Server Essentials Best Practices Analyzer](../migrate/Run-the-Windows-Server-Essentials-Best-Practices-Analyzer.md).  После завершения миграции параметров и данных на Windows Server Essentials, необходимо запустить анализатор соответствия Рекомендациям Windows Server Essentials.  

  
 Для выполнения некоторых процедур миграции нужно открыть окно командной строки от имени администратора.  
  
###  <a name="BKMK_OpenACommandPromptAsAdmin"></a>Чтобы открыть окно командной строки на исходном сервере от имени администратора  
  
1.  Нажмите кнопку **запустить**.  
  
2.  В поле поиска введите **cmd**.  
  
3.  В списке результатов щелкните правой кнопкой мыши **cmd**, а затем нажмите кнопку **Запуск от имени администратора**.  
  
#### <a name="to-open-a-command-prompt-window-on-the-destination-server-as-an-administrator"></a>Чтобы открыть окно командной строки на целевом сервере от имени администратора  
  
1.  На **запустить** экрана, в поле поиска введите **cmd**.  
  
2.  В списке результатов щелкните правой кнопкой мыши **cmd**, а затем нажмите кнопку **Запуск от имени администратора**.
