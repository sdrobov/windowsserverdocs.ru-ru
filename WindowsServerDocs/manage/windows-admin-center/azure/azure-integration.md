---
title: Настройка интеграции с Azure
description: Настройка Azure интеграции Windows Admin Center (проект Honolulu). Подключение к шлюз Windows Admin Center в Azure.
ms.technology: manage
ms.topic: article
author: haley-rowland
ms.author: harowl
ms.date: 09/19/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: 38b973680463cdebc1b3168e447abfcf1caba6b5
ms.sourcegitcommit: f1edfc6525e09dd116b106293f9260123a94de0c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "9296992"
---
# Настройка интеграции с Azure

>Относится к: Windows Admin Center, ознакомительная версия Windows Admin Center

Windows Admin Center поддерживает несколько дополнительных функций, которые интегрируются со службами Azure. [Узнайте об интеграции Azure параметров, доступных в Windows Admin Center.](../plan/azure-integration-options.md)

Чтобы разрешить шлюз Windows Admin Center для связи с Azure для использования проверки подлинности Azure Active Directory для доступа к шлюз, или для создания ресурсов Azure от вашего имени (например, чтобы защитить виртуальные машины под управлением Windows Admin Center с помощью Azure Site Восстановление), необходимо сначала зарегистрировать шлюз Windows Admin Center с помощью Azure. Необходимо выполнить это один раз для шлюз Windows Admin Center — параметра сохраняются при обновлении шлюз до более новой версии.

## Регистрация шлюз Azure

При первом использовании функции интеграции Azure в Windows Admin Center, вам будет предложено зарегистрировать шлюза к Azure. Также можно зарегистрировать шлюз, перейдя на вкладку " **Azure** " в параметрах Windows Admin Center.

Интерактивная действия в продукт создаст приложения Azure AD в каталог, который позволяет Windows Admin Center для обмена данными с помощью Azure. Чтобы просмотреть приложения Azure AD, создается автоматически, перейдите на вкладку **Azure** параметров Windows Admin Center. Гиперссылка **представления в Azure** позволяет просматривать приложения Azure AD на портале Azure. 

Приложение Azure AD, создан используется для всех точек Azure интеграции в Windows Admin Center, включая [аутентификацию Azure AD к шлюзу](../configure/user-access-control.md#azure-active-directory).