---
ms.assetid: 3a840b63-78b7-4e62-af7b-497026bfdb93
title: "Пошаговое руководство - управление рисками с использованием условного управления доступом"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 11d2d567f9264dca53a3426263a172649d7d7c11
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="walkthrough-guide-manage-risk-with-conditional-access-control"></a>Пошаговое руководство: Управление рисками с использованием условного управления доступом

>Область применения: Windows Server 2012 R2


## <a name="about-this-guide"></a>Об этом руководстве
Это пошаговое руководство содержит инструкции по управлению риском с использованием одного из факторов (данных пользователя), доступного в рамках механизма условного управления доступом в федерации служб Active Directory (AD FS) в Windows Server 2012 R2. Дополнительные сведения о механизмах условного доступа и авторизации в AD FS в Windows Server 2012 R2 см. в разделе [Manage Risk with Conditional Access Control](../../ad-fs/operations/Manage-Risk-with-Conditional-Access-Control.md).

Это пошаговое руководство состоит из следующих разделов:

-   [Шаг 1: Настройка лабораторной среды](../../ad-fs/operations/Walkthrough-Guide--Manage-Risk-with-Conditional-Access-Control.md#BKMK_1)

-   [Шаг 2: Проверка механизма управления доступом по умолчанию AD FS](../../ad-fs/operations/Walkthrough-Guide--Manage-Risk-with-Conditional-Access-Control.md#BKMK_2)

-   [Шаг 3: Настройка политики условного управления доступом на основе данных пользователя](../../ad-fs/operations/Walkthrough-Guide--Manage-Risk-with-Conditional-Access-Control.md#BKMK_3)

-   [Шаг 4: Проверка механизма условного управления доступом](../../ad-fs/operations/Walkthrough-Guide--Manage-Risk-with-Conditional-Access-Control.md#BKMK_4)

## <a name="BKMK_1"></a>Шаг 1: Настройка лабораторной среды
Для выполнения этого пошагового руководства вам потребуется среда, состоящая из следующих компонентов:

-   Домен Active Directory с помощью тестового пользователя и учетные записи групп, под управлением Windows Server 2008, Windows Server 2008 R2 или Windows Server 2012 со схемой, обновленной для Windows Server 2012 R2 или домен Active Directory, работающими под управлением Windows Server 2012 R2

-   Сервер федерации под управлением Windows Server 2012 R2

-   Веб-сервер, на котором размещен пример приложения

-   Клиентский компьютер, из которого можно получить доступ к примеру приложения

> [!WARNING]
> Настоятельно рекомендуется (как в средах производства или тестирования) следует использовать тот же компьютер в качестве сервера федерации и веб-сервера.

В этой среде сервер федерации выдает утверждения, которые требуются пользователям доступ к примеру приложения. Веб-сервере размещается пример приложения, которое будет считать доверенными пользователей, предъявивших утверждения, выданные сервером федерации.

Инструкции по настройке среды см. в разделе [Настройка лабораторной среды для служб AD FS в Windows Server 2012 R2](../../ad-fs/deployment/Set-up-the-lab-environment-for-AD-FS-in-Windows-Server-2012-R2.md).

## <a name="BKMK_2"></a>Шаг 2: Проверка механизма управления доступом по умолчанию AD FS
На этом шаге вы проверите механизма управления доступом AD FS, где пользователь перенаправляется на страницу входа Служб федерации Active Directory, по умолчанию предоставляет действительные учетные данные и предоставляется доступ к приложению. Можно использовать **Robert Hatley** учетной записи AD и **claimapp** образец приложения, которая настроена в [Настройка лабораторной среды для служб AD FS в Windows Server 2012 R2](../../ad-fs/deployment/Set-up-the-lab-environment-for-AD-FS-in-Windows-Server-2012-R2.md).

#### <a name="to-verify-the-default-ad-fs-access-control-mechanism"></a>Проверка по умолчанию механизма управления доступом AD FS

1.  На клиентском компьютере откройте окно браузера и перейдите к примеру приложения: **https://webserv1.contoso.com/claimapp**.

    Это действие автоматически перенаправляет запрос серверу федерации и вам предлагается выполнить вход с помощью имени пользователя и пароля.

2.  Введите учетные данные для **Robert Hatley** в созданную учетную запись AD [Настройка лабораторной среды для служб AD FS в Windows Server 2012 R2](../../ad-fs/deployment/Set-up-the-lab-environment-for-AD-FS-in-Windows-Server-2012-R2.md).

    Вам будет предоставлен доступ к приложению.

## <a name="BKMK_3"></a>Шаг 3: Настройка политики условного управления доступом на основе данных пользователя
На этом шаге вы настроите политику управления доступом на основе данных членства в группах пользователя. Другими словами, вы настроите **правило авторизации выдачи** на сервере федерации для доверия с проверяющей стороной, которое представляет ваш пример приложения — **claimapp**. Согласно этому правилу **Robert Hatley** пользователя AD будут выданы утверждения, которые требуются для доступа к приложению, так как он принадлежит к **процент** группы. Вы добавили **Robert Hatley** учетную запись **процент** в [Настройка лабораторной среды для служб AD FS в Windows Server 2012 R2](../../ad-fs/deployment/Set-up-the-lab-environment-for-AD-FS-in-Windows-Server-2012-R2.md).

Можно выполнить эту задачу, с помощью консоли управления AD FS или с помощью Windows PowerShell.

#### <a name="to-configure-conditional-access-control-policy-based-on-user-data-via-the-ad-fs-management-console"></a>Настройка политики условного управления доступом на основе данных пользователя с помощью консоли управления AD FS

1.  В консоли управления AD FS перейдите к **отношения доверия**, а затем **доверия с проверяющей стороной**.

2.  Выберите доверия проверяющей стороной, которое представляет ваш пример приложения (**claimapp**), а затем перейдите в **действия** области или щелкните правой кнопкой мыши отношение доверия с проверяющей стороной, выберите **изменение правил для утверждений**.

3.  В **изменение правил для утверждений для claimapp** выберите **правила авторизации выдачи** и щелкните **добавить правило**.

4.  В **выдачи утверждений мастера добавления правила авторизации**на **Выбор шаблона правила**выберите **разрешать или запрещать пользователям на основании входящего утверждения** шаблона правила для утверждений, а затем нажмите кнопку **Далее**.

5.  На **Настройка правила** , выполните все описанные ниже и нажмите кнопку **Готово**:

    1.  Введите имя правила для утверждений, например **TestRule**.

    2.  Выберите **SID группы** как **тип входящего утверждения**.

    3.  Нажмите кнопку **Обзор**, введите в **процент** для имени AD тестовой группы и разрешите его для **значение входящего утверждения** поле.

    4.  Выберите **запретить доступ пользователям с данным входящим утверждением** параметр.

6.  В **изменение правил для утверждений для claimapp** окно, не забудьте удалить **разрешить доступ всем пользователям** правила, созданные по умолчанию при создании доверия с проверяющей стороной.

#### <a name="to-configure-conditional-access-control-policy-based-on-user-data-via-windows-powershell"></a>Настройка политики условного управления доступом на основе данных пользователя с помощью Windows PowerShell

1.  На сервере федерации откройте окно команд Windows PowerShell и выполните следующую команду:


    `$rp = Get-AdfsRelyingPartyTrust -Name claimapp`


2.  В том же окне команд Windows PowerShell выполните следующую команду:


    `$GroupAuthzRule = '@RuleTemplate = "Authorization" @RuleName = "Foo" c:[Type == "https://schemas.microsoft.com/ws/2008/06/identity/claims/groupsid", Value =~ "^(?i)<group_SID>$"] =>issue(Type = "https://schemas.microsoft.com/authorization/claims/deny", Value = "DenyUsersWithClaim");'
    Set-AdfsRelyingPartyTrust -TargetRelyingParty $rp -IssuanceAuthorizationRules $GroupAuthzRule`

> [!NOTE]
> Убедитесь, что замените < group_SID > значением идентификатора безопасности для вашей Рекламы **процент** группы.

## <a name="BKMK_4"></a>Шаг 4: Проверка механизма условного управления доступом
На этом шаге вы проверите политики условного управления доступом, настроенную в предыдущем шаге. Можно использовать следующую процедуру, чтобы убедиться, что **Robert Hatley** пользователя AD можно получить доступ к вашему примеру приложения, так как он принадлежит к **процент** группы и пользователей AD, которые не принадлежат **процент** группы не имеют доступа к примеру приложения.

1.  На клиентском компьютере откройте окно браузера и перейдите к примеру приложения: **https://webserv1.contoso.com/claimapp**

    Это действие автоматически перенаправляет запрос серверу федерации и вам предлагается выполнить вход с помощью имени пользователя и пароля.

2.  Введите учетные данные для **Robert Hatley** в созданную учетную запись AD [Настройка лабораторной среды для служб AD FS в Windows Server 2012 R2](../../ad-fs/deployment/Set-up-the-lab-environment-for-AD-FS-in-Windows-Server-2012-R2.md).

    Вам будет предоставлен доступ к приложению.

3.  Введите учетные данные другого пользователя AD, который не принадлежит **процент** группы. (Дополнительные сведения о создании учетных записей пользователей в AD см. в разделе [https://technet.microsoft.com/library/cc7833232.aspx](https://technet.microsoft.com/library/cc783323%28v=ws.10%29.aspx).

    На этом этапе согласно политике управления доступом, настроенную в предыдущем шаге, сообщение «Отказано в доступе» отображается для этого пользователя AD, который не принадлежит **процент** группы. Текст сообщения по умолчанию **вас нет прав доступа к этому сайту. Щелкните здесь, чтобы выйти из системы и войти снова или обратитесь к администратору за разрешениями.** Тем не менее этот текст можно полностью настраивать. Дополнительные сведения о том, как настроить процесс входа в систему см. в разделе [настройка страниц AD FS Sign-in](https://technet.microsoft.com/library/dn280950.aspx).

## <a name="see-also"></a>См. также:
[Управление рисками с использованием условного управления доступом](../../ad-fs/operations/Manage-Risk-with-Conditional-Access-Control.md)
[Настройка лабораторной среды для служб AD FS в Windows Server 2012 R2](../deployment/Set-up-the-lab-environment-for-AD-FS-in-Windows-Server-2012-R2.md)


