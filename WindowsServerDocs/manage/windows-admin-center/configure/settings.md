---
title: Параметры
description: Сведения о параметрах в Windows Admin Center (проект Honolulu). Параметры пользователя позволяют пользователям изменять их языка или региона и другие параметры. Параметры шлюза Администраторы настроить шлюз.
ms.technology: manage
ms.topic: article
author: haley-rowland
ms.author: harowl
ms.date: 04/12/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: d67a2c743900792353141186112cd09dbf780309
ms.sourcegitcommit: f1edfc6525e09dd116b106293f9260123a94de0c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "9296626"
---
# Параметры Windows Admin Center

> Область применения: Windows Admin Center

Параметры Windows Admin Center состоят из параметры уровня пользователя и шлюза на уровне. Изменение уровня пользователя, не закрывая влияет только на профиль текущего пользователя, изменение параметра шлюза на уровне влияет на всех пользователей на этот шлюз Windows Admin Center.

## Параметры пользователя

Параметры уровня пользователя состоят из следующих разделов:

- Account
- Персонализация
- Язык и регион
- Предложения
- Дополнительно

На вкладке " **учетная запись** " пользователи могут только просматривать учетные данные, которые они использовали для проверки подлинности для Windows Admin Center. Если в качестве поставщика удостоверений Azure AD, пользователь может войти в за пределы свою учетную запись Azure AD на этой вкладке.

На вкладке " **Персонализация** " пользователи могут переключать темную тему пользовательского интерфейса.

На вкладке " **Язык и регион** " пользователи могут изменять форматы языка и региона, отображаются с Windows Admin Center.

На вкладке " **предложения** " пользователи могут переключать предложения о новых функций и служб Azure.

На вкладке " **Дополнительно** " дает разработчикам расширения Windows Admin Center дополнительных специальных возможностей.

## Параметры шлюза

Параметры уровня шлюза состоят из следующих разделов:

- Расширения
- Access
- Azure
- Общие подключения

Только шлюза администраторы могут просматривать и изменять эти параметры. Изменения этих параметров изменения конфигурации шлюза и применяются ко всем пользователям в шлюз Windows Admin Center.

На вкладке " **расширения** " Администраторы могут установки, удаления или обновления расширения шлюза. [Дополнительные сведения о расширениях.](using-extensions.md)

Вкладка **доступ** позволяет администраторам настраивать доступ к шлюзу Windows Admin Center, а также поставщика удостоверений, используемый для проверки подлинности пользователей. [Дополнительные сведения об управлении доступ к шлюзу.](user-access-control.md)

На вкладке " **Azure** " Администраторы можно зарегистрироваться шлюз Azure для включения [функции интеграции с Azure](azure-integration.md) в Windows Admin Center.

На вкладке " **Общие подключения** ", администраторы могут настроить один список подключений к совместно использовать на всех пользователей в шлюз Windows Admin Center. [Дополнительные сведения о настройке подключений один раз для всех пользователей шлюза.](shared-connections.md)