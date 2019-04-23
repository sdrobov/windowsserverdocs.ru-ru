---
title: Службы multiPoint Services — задачи, выполняемые после миграции
description: Узнайте, как проверить и закройте миграцию в MultiPoint Services
ms.custom: na
ms.date: 07/29/2016
ms.prod: windows-server-threshold
ms.technology: multipoint-services
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1497cae0-071e-467d-89b8-a7050815d7de
author: lizap
manager: dongill
ms.openlocfilehash: e3fa3c812355a14289ea4eeff3ab1e7e92e00d97
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59863505"
---
# <a name="multipoint-services---post-migration-tasks"></a>Службы multiPoint Services — задачи, выполняемые после миграции

>Область применения. Windows Server 2016

После переноса MultiPoint Services в Windows Server 2016, используйте следующие сведения для проверки миграции и выполните действия очистки.

## <a name="validate-the-migration-by-running-a-pilot-program"></a>Проверка миграции путем запуска пилотной программы

Вы можете проверить миграцию MultiPoint Services, создав пилотный проект в рабочей среде. Запустите пилотного проекта на серверах до ввода перенесенных служб ролей в эксплуатацию, чтобы убедиться, что развертывание работает должным образом. Рекомендуется ограничить число подключений на первый, медленно увеличения количества пользователей, обращающихся к MultiPoint Services.

> [!NOTE] 
> Всегда используйте тестовые учетные записи для проверки миграции. Используйте учетную запись с правами администратора и учетной записи для действительного пользователя.

## <a name="retire-the-source-server"></a>Прекращение использования исходного сервера
После проверки миграцию можно завершить работу или отключения исходного сервера из сети. Если серверу не присоединены к домену, удалите ее из домена перед отключением.

