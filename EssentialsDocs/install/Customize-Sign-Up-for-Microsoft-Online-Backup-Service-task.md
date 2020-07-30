---
title: Настройка задачи "Зарегистрироваться в Microsoft Online Backup Service"
description: Описание использования Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: a7eafbb3-7728-487e-b287-90bbd6fee7f0
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 77d1c98688f58e767d4ad76c0abf5456ef7ba052
ms.sourcegitcommit: d99bc78524f1ca287b3e8fc06dba3c915a6e7a24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/27/2020
ms.locfileid: "87181310"
---
# <a name="customize-sign-up-for-microsoft-online-backup-service-task"></a>Настройка задачи "Зарегистрироваться в Microsoft Online Backup Service"

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

По умолчанию при выборе задачи **Зарегистрироваться на Microsoft Online Backup Service** на вкладке **УСТРОЙСТВА** панели мониторинга открывается веб-сайт Microsoft Online Backup Service. На веб-сайте представлена информация о службе, предоставляется помощь в регистрации и загрузке необходимого программного обеспечения.

 Изменить настройки задачи **Зарегистрироваться на Microsoft Online Backup Service** можно двумя способами:

-   Можно заменить URL-адрес веб-сайта по умолчанию на URL-адрес, представляющий особое взаимодействие с пользователем. Чтобы изменить URL-адрес по умолчанию, откройте редактор реестра и создайте раздел реестра: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\OnlineBackup\LinkUrl**, а затем назначьте пользовательский URL-адрес в качестве значения реестра.

-   Задачу можно скрыть. Чтобы скрыть задачу, откройте редактор реестра и создайте раздел реестра: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\OnlineBackup\OnlineBackupInstalled**.

## <a name="see-also"></a>См. также:
 [Создание и Настройка образа](Creating-and-Customizing-the-Image.md) [Дополнительные настройки](Additional-Customizations.md) [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md) [Тестирование взаимодействия с пользователем](Testing-the-Customer-Experience.md)