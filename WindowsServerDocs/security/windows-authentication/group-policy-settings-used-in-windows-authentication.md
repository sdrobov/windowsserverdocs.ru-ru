---
title: "Параметры групповой политики в проверке подлинности Windows"
description: "Безопасность Windows Server"
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: security-windows-auth
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9e237f89-45b1-4a4e-9b72-11dc7d6a470b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/12/2016
ms.openlocfilehash: 38df2033b57c0394b96f539f54efe6a3579500f2
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="group-policy-settings-used-in-windows-authentication"></a>Параметры групповой политики в проверке подлинности Windows

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

В этом справочном разделе для ИТ-специалистов описывается использование и влияние параметров групповой политики в процессе проверки подлинности.

Проверка подлинности в операционных системах Windows можно управлять путем добавления в группы пользователей, компьютеров и учетных записей служб, а затем путем применения политик проверки подлинности для этих групп. Эти политики определяются как локальные политики безопасности, а как административные шаблоны, также известные как параметры групповой политики. Оба набора можно настроить и распространяемые в масштабах организации с помощью групповой политики.

> [!NOTE]
> Компоненты, появившиеся в Windows Server 2012 R2 позволяют настроить политики проверки подлинности для целевых служб или приложений, обычно называется приемников проверки подлинности, с помощью защищенных учетных записей. Сведения о том, как это сделать в Active Directory см. в разделе [Настройка защищенных учетных записей](how-to-configure-protected-accounts.md).

Например можно применить следующие политики для группы, на основании их функции в организации:

-   Войдите в систему локально или к домену

-   Вход в систему через сеть

-   Сброс учетных записей

-   Создание учетных записей

В следующей таблице перечислены группы политик, связанные с проверкой подлинности и приводятся ссылки на документацию, которая поможет вам настроить этих политик.

|Группа политик|Расположение|Описание|
|--------|------|--------|
|**Политики паролей**|Локального компьютера\Конфигурация конфигурация Settings\Security учетных политики компьютера|Влияет на политики паролей, характеристики и поведение паролей. Политики паролей используются для учетных записей домена или учетные записи локальных пользователей. Они определяют параметры для паролей, такие как применение и срок действия.<br /><br />Сведения о конкретных параметрах см. в разделе [политики паролей](https://technet.microsoft.com/itpro/windows/keep-secure/password-policy).|
|**Политики блокировки учетных записей**|Локального компьютера\Конфигурация конфигурация Settings\Security учетных политики компьютера|Параметры политики блокировки учетной записи отключите учетные записи после заданного числа неудачных попыток входа. С помощью этих параметров поможет вам определить и заблокировать попыток взлома паролей.<br /><br />Сведения о параметрах политики блокировки учетной записи см. в разделе [политики блокировки учетных записей](https://technet.microsoft.com/itpro/windows/keep-secure/account-lockout-policy).|
|**Политика Kerberos**|Локального компьютера\Конфигурация конфигурация Settings\Security учетных политики компьютера|Параметры, связанные с Kerberos включают билета время существования и принудительного применения правила. Политика Kerberos не относится к локальной учетной записи базы данных, поскольку протокол проверки подлинности Kerberos не используется для проверки подлинности локальных учетных записей. Таким образом параметры политики Kerberos можно настроить только с помощью групповой политики объект (GPO), где она затрагивает входов в домен домена по умолчанию.<br /><br />Сведения о параметрах политики Kerberos для контроллера домена см. в разделе [политика Kerberos](https://technet.microsoft.com/itpro/windows/keep-secure/kerberos-policy).|
|**Политики аудита**|Локальный компьютер политика Конфигурация компьютера\Параметры Windows\Параметры безопасности\Локальные Политики\политика|Политика аудита позволяет контролировать и понять, доступ к объектам, такие как файлы и папки, а также для управления учетными записями пользователей и групп и вход пользователей в систему и выход из системы. Политики аудита можно указать категории событий для аудита, задайте размер и поведение журнала безопасности и определить, какие объекты, которые требуется отслеживать доступ и какой тип доступа, вы хотите отслеживать.<br /><br />|
|**Назначение прав пользователя**|Локальный компьютер политика Конфигурация компьютера\Параметры Windows\Параметры безопасности\Локальные Политики\назначение прав|Как правило, права пользователей назначаются на основании группы безопасности, к которым принадлежит пользователь, таких как Администраторы "," Опытные пользователи "или" пользователи. Чтобы предоставить или запретить разрешение на доступ к компьютеру, в зависимости от метода членства в группах безопасности и доступа к обычно используются параметры политики в этой категории.|
|**Параметры безопасности**|Локальный компьютер политика Конфигурация компьютера\Параметры Windows\Параметры безопасности\Локальные Политики\параметры|Политики, связанные с проверкой подлинности включают:<br /><br />-Устройств<br />-Контроллер домена<br />-Член домена<br />-Интерактивный вход в систему<br />-Сервер сети Microsoft<br />— Доступ к сети<br />-Сетевой безопасности<br />-Консоль восстановления<br />-Завершения работы<br /><br />|
|**Делегирования учетных данных**|Делегирование шаблоны\система\передача учетных Конфигурация компьютера|Делегирование учетных данных — это механизм, который позволяет использовать в других системах, наиболее заметно рядовых серверов и контроллеров домена в домене локальные учетные данные. Эти параметры применяются к приложениям с помощью учетных данных поставщика поддержки безопасности (SSP учетных данных). Подключение к удаленному рабочему столу приведен пример.|
|**KDC**|Конфигурация компьютера\Административные Templates\System\KDC компьютера|Эти параметры политики влияют на способ распространения ключей центра (KDC), которая является службой на контроллере домена, обрабатывает запросы на проверку подлинности Kerberos.|
|**Kerberos**|Конфигурация компьютера\Административные Templates\System\Kerberos компьютера|Эти параметры политики влияют на настройку Kerberos для обработки поддержка утверждений, защита Kerberos, комплексной проверки подлинности, идентифицирующие прокси-серверов и других конфигураций.|
|**Вход в систему**|Конфигурация компьютера\Административные шаблоны\Система\Вход компьютера|Эти параметры политики определяют, как система представляется процесс входа в систему для пользователей.|
|**Сетевого входа в систему**|Вход в систему Templates\System\Net Конфигурация компьютера|Эти параметры политики определяют, как система обрабатывает запросы входа сети, включая поведением локатора контроллеров домена.<br /><br />Дополнительные сведения об использовании локатора контроллеров домена в процесс репликации см. в разделе [общее представление о межсайтовой репликации](https://technet.microsoft.com/library/cc771251.aspx).|
|**Биометрические данные**|Компьютер Конфигурация компьютера\Административные шаблоны\Компоненты Components\Biometrics|Эти параметры политики, как правило разрешить или запретить использование биометрических данных для проверки подлинности.<br /><br />Сведения о реализации Windows биометрических данных см. в разделе Обзор биометрической платформы Windows.|
|**Пользовательский интерфейс учетных данных**|Компьютер Конфигурация компьютера\Административные шаблоны\Компоненты windows\пользовательский интерфейс учетных данных|Эти параметры политики определяют, как управление учетными данными в момент записи.|
|**Синхронизация паролей**|Компьютер Конфигурация компьютера\Административные шаблоны\Компоненты Components\Password синхронизации|Эти параметры политики определяют, как система управляет синхронизации паролей между Windows и операционных систем на базе UNIX.<br /><br />Дополнительные сведения см. в разделе [синхронизации паролей](https://technet.microsoft.com/library/cc732609.aspx).|
|**Смарт-карты**|Компьютер Конфигурация компьютера\Административные шаблоны\Компоненты Components\Smart карты|Эти параметры политики определяют, как система управляет входов смарт-карты.<br /><br />|
|**Параметры входа в систему Windows**|Параметры компьютера Конфигурация компьютера\Административные шаблоны\Компоненты Components\Windows входа в систему|Эти параметры политики определяют время и способ возможности входа в систему.|
|**Ctrl + Alt + Del параметры**|Конфигурация компьютера\Административные шаблоны\Компоненты Components\Ctrl + Alt + Del параметров|Эти параметры политики влияют на внешний вид и доступ к функциям, при входе в систему пользовательского интерфейса (безопасном рабочем столе), такие как диспетчер задач и блокировки клавиатуры компьютера.|
|**Вход в систему**|Компьютер Конфигурация компьютера\Административные шаблоны\Компоненты Components\Logon|Эти параметры политики определяют, если или какие процессы могут выполняться при входе пользователя в систему.|

## <a name="see-also"></a>См. также:
[Технический обзор проверки подлинности Windows](windows-authentication-technical-overview.md)

