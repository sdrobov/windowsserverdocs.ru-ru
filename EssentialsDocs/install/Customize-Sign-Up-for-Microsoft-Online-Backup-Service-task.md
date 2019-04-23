---
title: Настройка задачи "Зарегистрироваться в Microsoft Online Backup Service"
description: Описывает способ использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a7eafbb3-7728-487e-b287-90bbd6fee7f0
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: cd148e0e58cd80dbff7f7884ead95dc1e46b6257
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59879935"
---
# <a name="customize-sign-up-for-microsoft-online-backup-service-task"></a>Настройка задачи "Зарегистрироваться в Microsoft Online Backup Service"

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

По умолчанию при выборе задачи **Зарегистрироваться на Microsoft Online Backup Service** на вкладке **УСТРОЙСТВА** панели мониторинга открывается веб-сайт Microsoft Online Backup Service. На веб-сайте представлена информация о службе, предоставляется помощь в регистрации и загрузке необходимого программного обеспечения.  
  
 Изменить настройки задачи **Зарегистрироваться на Microsoft Online Backup Service** можно двумя способами:  
  
-   Можно заменить URL-адрес веб-сайта по умолчанию на URL-адрес, представляющий особое взаимодействие с пользователем. Чтобы изменить URL-адрес по умолчанию, откройте редактор реестра и создайте раздел реестра: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\OnlineBackup\LinkUrl**, а затем назначьте пользовательский URL-адрес в качестве значения для раздела.  
  
-   Задачу можно скрыть. Чтобы скрыть задачу, откройте редактор реестра и создайте раздел реестра: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\OnlineBackup\OnlineBackupInstalled**.  
  
## <a name="see-also"></a>См. также  
 [Создание и настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)