---
title: Настройка интеграции с Azure
description: Настройка службы интеграции Azure в центре администрирования Windows (проект Хонолулу). Подключение шлюза центра администрирования Windows к Azure.
ms.technology: manage
ms.topic: article
author: haley-rowland
ms.author: harowl
ms.date: 09/19/2018
ms.localizationpriority: medium
ms.prod: windows-server
ms.openlocfilehash: 448a8fb3e4340752b673b06f86d5d49211b6b147
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71357356"
---
# <a name="configuring-azure-integration"></a>Настройка интеграции с Azure

>Область применения. Windows Admin Center, ознакомительная версия Windows Admin Center

Центр администрирования Windows поддерживает несколько дополнительных функций, которые интегрируются со службами Azure. [Узнайте о вариантах интеграции с Azure, доступных в центре администрирования Windows.](../plan/azure-integration-options.md)

Чтобы разрешить шлюзу центра администрирования Windows взаимодействовать с Azure для использования проверки подлинности Azure Active Directory для доступа к шлюзу или для создания ресурсов Azure от вашего имени (например, для защиты виртуальных машин, управляемых в центре администрирования Windows с помощью сайта Azure) Recovery), необходимо сначала зарегистрировать шлюз центра администрирования Windows в Azure. Это необходимо сделать только один раз для шлюза центра администрирования Windows — параметр сохраняется при обновлении шлюза до более новой версии.

## <a name="register-your-gateway-with-azure"></a>Регистрация шлюза в Azure

При первой попытке использовать функцию интеграции с Azure в центре администрирования Windows вам будет предложено зарегистрировать шлюз в Azure. Вы также можете зарегистрировать шлюз, перейдя на вкладку **Azure** в разделе Параметры центра администрирования Windows.

В разделе "Интерактивные шаги для продукта" будет создано приложение Azure AD в каталоге, позволяющее центру администрирования Windows обмениваться данными с Azure. Чтобы просмотреть автоматически созданное приложение Azure AD, перейдите на вкладку **Azure** в окне параметров центра администрирования Windows. С помощью гиперссылки **представление в Azure** вы можете просмотреть приложение Azure AD в портал Azure. 

Созданное приложение Azure AD используется для всех точек интеграции Azure в центре администрирования Windows, включая [аутентификацию Azure AD в шлюзе](../configure/user-access-control.md#azure-active-directory).