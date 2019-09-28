---
title: Службы MultiPoint — задачи, выполняемые после миграции
description: Узнайте, как проверить и закрыть миграцию в службы MultiPoint.
ms.custom: na
ms.date: 07/29/2016
ms.prod: windows-server
ms.technology: multipoint-services
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1497cae0-071e-467d-89b8-a7050815d7de
author: lizap
manager: dongill
ms.openlocfilehash: 3102a442b4668856050f603f30f57f6bbed20654
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71389021"
---
# <a name="multipoint-services---post-migration-tasks"></a>Службы MultiPoint — задачи, выполняемые после миграции

>Область применения. Windows Server 2016

После миграции на службы MultiPoint в Windows Server 2016 используйте следующие сведения для проверки миграции и выполнения действий по очистке.

## <a name="validate-the-migration-by-running-a-pilot-program"></a>Проверка миграции путем запуска пилотной программы

Вы можете проверить миграцию служб MultiPoint, создав пилотный проект в рабочей среде. Запустите пилотный проект на серверах перед тем, как перевести перенесенные службы ролей в рабочую среду, чтобы убедиться, что развертывание работает должным образом. Рассмотрите возможность ограничения числа подключений в первую очередь, постепенно увеличивая число пользователей, обращающихся к службам MultiPoint.

> [!NOTE] 
> Всегда используйте тестовые учетные записи для тестирования миграции. Используйте учетную запись с правами администратора и учетную запись для допустимого пользователя.

## <a name="retire-the-source-server"></a>Прекращение использования исходного сервера
После проверки миграции можно завершить работу или отключить исходный сервер от сети. Если сервер был присоединен к домену, удалите его из домена перед отключением.

