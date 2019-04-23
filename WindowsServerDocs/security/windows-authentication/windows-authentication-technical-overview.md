---
title: Технический обзор проверки подлинности Windows
description: Безопасность Windows Server
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: security-windows-auth
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 286d3e41-434f-4703-9320-706d06ebda51
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/12/2016
ms.openlocfilehash: 1be96846596900c7b2eb2d9d5da93e75572aac98
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59879255"
---
# <a name="windows-authentication-technical-overview"></a>Технический обзор проверки подлинности Windows

>Область применения. Windows Server (полугодовой канал), Windows Server 2016

В этом разделе для ИТ-специалистов ссылки на разделы Технический обзор проверки подлинности Windows. Проверка подлинности Windows — это процесс, чтобы подтвердить подлинность пользователя или службы, пытающихся получить доступ к Windows.

В этих разделах описывается архитектура проверки подлинности Windows и его компонентов.

Чтобы сохранить в цифровом виде или распечатать страницы из этой библиотеки, нажмите кнопку **Экспорт** (в правом верхнем углу страницы) и следуйте инструкциям.

-   [Различия в проверке подлинности Windows между операционными системами Windows](https://technet.microsoft.com/library/dn169017.aspx)

    Описываются важные различия в архитектура проверки подлинности и процессах.

-   [Основные понятия проверки подлинности Windows](https://technet.microsoft.com/library/dn169018.aspx)

    Описываются основные понятия, на какие Windows проверка подлинности основана.

-   [Сценарии проверки подлинности для входа в систему Windows](https://technet.microsoft.com/library/dn169020.aspx)

    Перечислены различные сценарии входа в систему.

-   [Архитектура проверки подлинности Windows](https://technet.microsoft.com/library/dn169024.aspx)

    Описываются важные различия в архитектуре проверки подлинности и процессы для операционных систем Windows.

    -   [Архитектура интерфейса поставщика поддержки безопасности](https://technet.microsoft.com/library/dn169026.aspx)

        Описывается архитектура SSPI.

    -   [Процедуры с учетными данными в проверке подлинности Windows](https://technet.microsoft.com/library/dn169014.aspx)

        Описывает процессы управления другие учетные данные.

-   [Групповые политики проверки подлинности Windows](https://technet.microsoft.com/library/dn169021.aspx)

    Описывает использование и влияние групповые политики в процессе проверки подлинности.

## <a name="what-is-not-covered"></a>Неохваченные темы
В этих разделах рассматриваются процедуры по разработке и реализации мониторинга ваших технологий проверки подлинности в среде Windows.

-   О разработки стратегии авторизации Windows, см. в разделе [Разработка стратегии авторизации ресурсов](https://technet.microsoft.com/library/cc783368.aspx).

-   О разработки стратегии проверки подлинности Windows, см. в разделе [Разработка стратегии проверки подлинности](https://technet.microsoft.com/library/cc758124.aspx).

-   О разработки стратегии реализации инфраструктуры открытых ключей Windows, см. в разделе [проектирование инфраструктуры открытого ключа](https://technet.microsoft.com/library/cc773138.aspx).

-   Для настройки и отслеживания безопасности, включая проверку подлинности, в среде Windows, см. в разделе:

    -   [Руководство по безопасности Windows XP](https://www.microsoft.com/download/details.aspx?id=962)

    -   [Базовой конфигурации системы безопасности Windows Vista](https://technet.microsoft.com/library/dd450978.aspx)

    -   [Базовой конфигурации системы безопасности Windows Server 2003](https://technet.microsoft.com/library/cc163140.aspx) и [угрозы и меры противодействия](https://technet.microsoft.com/library/dd162275.aspx)

    -   [Руководство по безопасности Windows Server 2008](https://www.microsoft.com/download/details.aspx?id=17606)

    -   [Базовой конфигурации системы безопасности Windows Server 2008 R2](https://technet.microsoft.com/library/gg236605.aspx)

-   Сведения об аудите события входа в систему и проверки подлинности в Windows см. в разделе [аудит событий безопасности](https://technet.microsoft.com/library/cc776394.aspx).


