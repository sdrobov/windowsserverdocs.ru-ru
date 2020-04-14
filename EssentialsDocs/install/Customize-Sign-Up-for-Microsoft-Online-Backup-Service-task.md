---
title: Настройка задачи "Зарегистрироваться в Microsoft Online Backup Service"
description: Описание использования Windows Server Essentials
ms.date: 10/03/2016
ms.prod: windows-server
ms.topic: article
ms.assetid: a7eafbb3-7728-487e-b287-90bbd6fee7f0
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 3318ca3937cdc054889121a830bc3eafec4d6acf
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80818087"
---
# <a name="customize-sign-up-for-microsoft-online-backup-service-task"></a>Настройка задачи "Зарегистрироваться в Microsoft Online Backup Service"

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

По умолчанию при выборе задачи **Зарегистрироваться на Microsoft Online Backup Service** на вкладке **УСТРОЙСТВА** панели мониторинга открывается веб-сайт Microsoft Online Backup Service. На веб-сайте представлена информация о службе, предоставляется помощь в регистрации и загрузке необходимого программного обеспечения.  
  
 Изменить настройки задачи **Зарегистрироваться на Microsoft Online Backup Service** можно двумя способами:  
  
-   Можно заменить URL-адрес веб-сайта по умолчанию на URL-адрес, представляющий особое взаимодействие с пользователем. Чтобы изменить URL-адрес по умолчанию, откройте редактор реестра и создайте раздел реестра: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\OnlineBackup\LinkUrl**, а затем назначьте пользовательский URL-адрес в качестве значения реестра.  
  
-   Задачу можно скрыть. Чтобы скрыть задачу, откройте редактор реестра и создайте раздел реестра: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\OnlineBackup\OnlineBackupInstalled**.  
  
## <a name="see-also"></a>См. также  
 [Создание и Настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа к развертыванию](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)