---
title: "Обзор протокола NTLM"
description: "Безопасность Windows Server"
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: security-kerberos
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 773909fd-c0bc-498a-95fc-bb452ec04d90
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/12/2016
ms.openlocfilehash: 523fb71304ae55d17203cab4d1c5a17551bf8fdf
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="ntlm-overview"></a>Обзор протокола NTLM

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

В этом разделе для ИТ-специалистов, описывает NTLM, любые изменения в функциональности и приводятся ссылки на технические ресурсы на проверку подлинности Windows и NTLM для Windows Server 2012 и предыдущих версий.

## <a name="BKMK_OVER"></a>Описание компонентов
Проверка подлинности NTLM — это семейство протоколов проверки подлинности, включенных в Windows Msv1\_0.dll. Протоколы проверки подлинности NTLM включают LAN Manager версий 1 и 2 и NTLM версий 1 и 2. Протоколы проверки подлинности NTLM, проверку подлинности пользователей и компьютеров, основываясь на механизме challenge\ и ответ, который доказывает серверу или контроллеру домена, что пользователю известен пароль, связанный с учетной записью. При использовании протокола NTLM сервер ресурсов должен выполнять одно из следующих действий для проверки удостоверения пользователя или компьютера, при необходимости новый маркер доступа:

-   Свяжитесь со службой проверки подлинности домена на контроллере домена, домен учетной записи компьютера или пользователя, если учетная запись является учетной записью домена.

-   Найдите учетную запись компьютера или пользователя в базе данных локальной учетной записи, если учетная запись является локальной учетной записи.

## <a name="BKMK_APP"></a>Текущие приложения
Проверка подлинности NTLM по-прежнему поддерживается и должен использоваться для проверки подлинности Windows с системами, настроенными как элемент рабочей группы. Проверка подлинности NTLM также используется для аутентификации при локальном входе на контроллеры домена отличных. Проверка подлинности Kerberos версии 5 является предпочтительным методом аутентификации в средах Active Directory, но отличных корпорацией Майкрософт или приложения Microsoft может по-прежнему использовать NTLM.

Чтобы сократить использование протокола NTLM в ИТ-среде необходимо обоих знать требования развернутых приложений NTLM и стратегии и шаги, необходимые для настройки вычислительных сред, использующих другие протоколы. Были добавлены новые инструменты и параметры, которые помогут вам понять принципы использования NTLM и выборочно ограничить трафик NTLM. Сведения о том, как анализировать и ограничивать использование NTLM в своих средах см. в разделе [Знакомство ограниченного использования программ для проверки подлинности NTLM](https://technet.microsoft.com/library/dd560653(v=ws.10).aspx) для доступа к аудиту и ограничению руководство по использованию NTLM.

## <a name="BKMK_NEW"></a>Новые и измененные функции
Отсутствуют изменения в функционале NTLM для Windows Server 2012.

## <a name="BKMK_DEP"></a>Удаленные или устаревшие функции
Нет не удаленные или нерекомендуемые функции NTLM для Windows Server 2012.

## <a name="BKMK_INSTALL"></a>Сведения о диспетчере сервера
NTLM нельзя использовать с помощью диспетчера сервера. Можно использовать параметры политики безопасности или групповые политики для управления использованием проверки подлинности NTLM между компьютерными системами. В домене протокол проверки подлинности по умолчанию является Kerberos.

## <a name="BKMK_LINKS"></a>См. также:
В следующей таблице перечислены материалы по NTLM и другим технологиям проверки подлинности Windows.

|Тип содержимого|Ссылки|
|--------|-------|
|**Период пробного использования продукта**|[Введение в ограничении аутентификации NTLM](https://technet.microsoft.com/library/dd560653.aspx)<br /><br />[Изменения в аутентификации NTLM](https://technet.microsoft.com/library/dd566199.aspx)|
|**Планирование**|[Руководство по моделированию угроз инфраструктуры ИТ](https://technet.microsoft.com/library/dd941826.aspx)<br /><br />[Угрозы и меры противодействия: параметры безопасности в Windows Server 2003 и Windows XP](https://technet.microsoft.com/library/dd162275.aspx)<br /><br />[Угрозы и противодействия: параметры безопасности в Windows Server 2008 и Windows Vista](https://technet.microsoft.com/library/dd349791.aspx)<br /><br />[Угрозы и противодействия: параметры безопасности в Windows Server 2008 R2 и Windows 7](https://technet.microsoft.com/library/hh125921.aspx)|
|**Развертывания**|[Расширенная защита для проверки подлинности](https://support.microsoft.com/kb/968389)<br /><br />[Аудиту и ограничению руководство по использованию NTLM](https://technet.microsoft.com/library/jj865674(v=ws.10).aspx)<br /><br />[Задать вопрос группе разработчиков служб каталогов: блокировка NTLM и вы: методики в Windows 7 анализа приложений и аудита](https://blogs.technet.com/askds/archive/2009/10/08/ntlm-blocking-and-you-application-analysis-and-auditing-methodologies-in-windows-7.aspx)<br /><br />[Блог, посвященный аутентификации Windows](https://blogs.technet.com/authentication/)<br /><br />[Настройка MaxConcurrentAPI для проверки подлинности NTLM через pass\](https://social.technet.microsoft.com/wiki/contents/articles/9759.configuring-maxconcurrentapi-for-ntlm-pass-through-authentication.aspx)|
|**Разработки**|[\(Windows\) Microsoft NTLM](https://msdn.microsoft.com/library/aa378749(VS.85).aspx)<br /><br />[\[MS\-NLMP\]: спецификация протокола проверки подлинности NT LAN Manager \(NTLM\)](https://msdn.microsoft.com/library/cc236621(PROT.10).aspx)<br /><br />[\[MS\-NNTP\]: проверка подлинности NT LAN Manager \(NTLM\): сети \(NNTP\) расширение протокола](https://msdn.microsoft.com/library/cc236774(PROT.10).aspx)<br /><br />[\[MS\-NTHT\]: спецификация протокола HTTP NTLM Over](https://msdn.microsoft.com/library/cc237488(PROT.10).aspx)|
|**Устранение неполадок**|На данный момент недоступно|
|**Ресурсы сообщества**|[Том же: "узкие места" NTLM и среда выполнения RPC](http://blogs.technet.com/b/askds/archive/2011/09/15/is-this-horse-dead-yet-ntlm-bottlenecks-and-the-rpc-runtime.aspx)|



