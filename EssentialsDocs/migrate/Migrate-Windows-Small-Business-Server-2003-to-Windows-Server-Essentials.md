---
title: Миграция с Windows Small Business Server 2003 на Windows Server Essentials
description: Описывает способ использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 119a7fbc-2c76-4aa3-8a7f-c7073d461b5b
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 83a7f45e91516621400e94c873d59d7cb6976702
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59846605"
---
# <a name="migrate-windows-small-business-server-2003-to-windows-server-essentials"></a>Миграция с Windows Small Business Server 2003 на Windows Server Essentials

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

В этом руководстве описывается, как выполнить миграцию существующего домена Windows SBS 2003 в Windows Server® 2012 Essentials на новом оборудовании, а затем перенести параметры и данные. В этом руководстве также описывается удалить существующий сервер из сети Windows Server Essentials после завершения миграции.  
  
> [!IMPORTANT]
>   Windows Server Essentials требуется 64-разрядной среде.  Windows Server Essentials не поддерживает 32-разрядной среде.  
  
> [!NOTE]
>  Во избежание проблем во время миграции группа разработки продукта Windows Server Essentials настоятельно рекомендует читать этот документ, прежде чем приступить к переносу.  
  
> [!NOTE]

>  Чтобы перенести данные сервера в последнюю версию Windows Server Essentials, см. в разделе [миграции на Windows Server Essentials](Migrate-from-Previous-Versions-to-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md).  

>  Чтобы перенести данные сервера в последнюю версию Windows Server Essentials, см. в разделе [миграции на Windows Server Essentials](../migrate/Migrate-from-Previous-Versions-to-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md).  

  
## <a name="additional-resources"></a>Дополнительные ресурсы  
 Ссылки на дополнительные сведения, инструменты и ресурсы сообщества, которые помогут вам выполнить процесс миграции, см. в статье [миграция Windows Small Business Server](https://go.microsoft.com/fwlink/?LinkId=217520) веб-сайта.  
  
## <a name="terms-and-definitions"></a>Термины и определения  
 **Исходный сервер:** существующий сервер, с которого выполняется миграция параметров и данных.  
  
 **Конечный сервер:** новый сервер, на который выполняется миграция параметров и данных.  
  
## <a name="migration-process-summary"></a>Сводка по процессу миграции  
 Настоящее руководство по миграции состоит из следующих разделов.  
  

1.  [Подготовка к миграции исходного сервера для Windows Server Essentials](Prepare-your-Source-Server-for-Windows-Server-Essentials-migration.md).  Убедитесь, что исходный сервер и сеть готовы к миграции. В этом разделе подробно описаны архивация параметров исходного сервера, проверка работоспособности его системы, установка последних пакетов обновления и исправлений, а также проверка параметров сети.  
  
2.  [Установка Windows Server Essentials в режиме миграции](Install-Windows-Server-Essentials-in-migration-mode.md).  В этом разделе описываются шаги, которые следует предпринять, чтобы установить Windows Server Essentials на конечном сервере в режиме миграции.  
  
3.  [Присоединение компьютеров к новой сети Windows Server Essentials](Join-computers-to-the-new-Windows-Server-Essentials-network.md).  В этом разделе рассматриваются присоединении клиентских компьютеров к новой сети Windows Server Essentials и обновления параметров групповой политики.  
  
4.  [Перемещение параметров и данных SBS 2003 на целевой сервер](Move-Windows-SBS-2003-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md).  Этот раздел содержит сведения о переносе данных и параметров с исходного сервера.  
  
5.  [Включение перенаправления папок на целевом сервере Windows Server Essentials](Enable-folder-redirection-on-the-Windows-Server-Essentials-Destination-Server.md).  Если перенаправление папок включено на исходном сервере, его можно включить на конечном сервере и затем удалить старый параметр групповой политики "Перенаправление папок".  
  
6.  [Понижение уровня и удаление исходного сервера из новой сети Windows Server Essentials](Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md).  Прежде чем удалить исходный сервер из сети, необходимо принудительно обновить групповую политику и понизить уровень исходного сервера.  
  
7.  [Выполнение задач после миграции для миграции Windows Server Essentials](Perform-post-migration-tasks-for-Windows-Server-Essentials-migration.md).  Завершив миграцию всех параметров и данных на Windows Server Essentials, вы можете сопоставить разрешенные компьютеры с учетными записями пользователей.  
  
8.  [Запустите Windows Server Essentials Best Practices Analyzer](Run-the-Windows-Server-Essentials-Best-Practices-Analyzer.md).  После завершения миграции параметров и данных на Windows Server Essentials, необходимо загрузить и запустить анализатор соответствия Рекомендациям Windows Server Essentials.  

1.  [Подготовка к миграции исходного сервера для Windows Server Essentials](../migrate/Prepare-your-Source-Server-for-Windows-Server-Essentials-migration.md).  Убедитесь, что исходный сервер и сеть готовы к миграции. В этом разделе подробно описаны архивация параметров исходного сервера, проверка работоспособности его системы, установка последних пакетов обновления и исправлений, а также проверка параметров сети.  
  
2.  [Установка Windows Server Essentials в режиме миграции](../migrate/Install-Windows-Server-Essentials-in-migration-mode.md).  В этом разделе описываются шаги, которые следует предпринять, чтобы установить Windows Server Essentials на конечном сервере в режиме миграции.  
  
3.  [Присоединение компьютеров к новой сети Windows Server Essentials](../migrate/Join-computers-to-the-new-Windows-Server-Essentials-network.md).  В этом разделе рассматриваются присоединении клиентских компьютеров к новой сети Windows Server Essentials и обновления параметров групповой политики.  
  
4.  [Перемещение параметров и данных SBS 2003 на целевой сервер](../migrate/Move-Windows-SBS-2003-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md).  Этот раздел содержит сведения о переносе данных и параметров с исходного сервера.  
  
5.  [Включение перенаправления папок на целевом сервере Windows Server Essentials](../migrate/Enable-folder-redirection-on-the-Windows-Server-Essentials-Destination-Server.md).  Если перенаправление папок включено на исходном сервере, его можно включить на конечном сервере и затем удалить старый параметр групповой политики "Перенаправление папок".  
  
6.  [Понижение уровня и удаление исходного сервера из новой сети Windows Server Essentials](../migrate/Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md).  Прежде чем удалить исходный сервер из сети, необходимо принудительно обновить групповую политику и понизить уровень исходного сервера.  
  
7.  [Выполнение задач после миграции для миграции Windows Server Essentials](../migrate/Perform-post-migration-tasks-for-Windows-Server-Essentials-migration.md).  Завершив миграцию всех параметров и данных на Windows Server Essentials, вы можете сопоставить разрешенные компьютеры с учетными записями пользователей.  
  
8.  [Запустите Windows Server Essentials Best Practices Analyzer](../migrate/Run-the-Windows-Server-Essentials-Best-Practices-Analyzer.md).  После завершения миграции параметров и данных на Windows Server Essentials, необходимо загрузить и запустить анализатор соответствия Рекомендациям Windows Server Essentials.  

  
 Для выполнения некоторых процедур миграции нужно открыть окно командной строки от имени администратора.  
  
###  <a name="BKMK_OpenACommandPromptAsAdmin"></a> Чтобы открыть окно командной строки на исходном сервере с правами администратора  
  
1.  Нажмите кнопку "Пуск".  
  
2.  В поле поиска введите "cmd".  
  
3.  В списке результатов щелкните правой кнопкой мыши команду cmd и выберите пункт "Запуск от имени администратора".  
  
#### <a name="to-open-a-command-prompt-window-on-the-destination-server-as-an-administrator"></a>Открытие окна командной строки на конечном сервере от имени администратора  
  
1.  На **начальном экране** в поле поиска введите **cmd**.  
  
2.  В списке результатов правой кнопкой мыши щелкните команду **cmd**и выберите пункт **Запуск от имени администратора**.
