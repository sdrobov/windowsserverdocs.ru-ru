---
title: Обзор протокола NTLM
description: Безопасность Windows Server
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
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59890645"
---
# <a name="ntlm-overview"></a>Обзор протокола NTLM

>Область применения. Windows Server (полугодовой канал), Windows Server 2016

В этом разделе для ИТ-специалистов, описывает NTLM, любые изменения в функциональности и ссылки на технические ресурсы для проверки подлинности Windows и NTLM для Windows Server 2012 и предыдущих версий.

## <a name="BKMK_OVER"></a>Описание компонента
Проверка подлинности NTLM — это семейство протоколов проверки подлинности, реализованные в Windows Msv1\_0.dll. Протоколы проверки подлинности NTLM включают LAN Manager версий 1 и 2, а также NTLM версий 1 и 2. Протоколы проверки подлинности NTLM, проверки подлинности пользователей и компьютеров, основываясь на запрос\/механизме ответа, который доказывает серверу или контроллеру домена, что пользователю известен пароль, связанный с учетной записью. При использовании протокола NTLM сервер ресурсов должен выполнять одно из следующих действий для проверки удостоверения пользователя или компьютера каждый раз, как возникает необходимость в новом маркере доступа:

-   Свяжитесь со службой проверки подлинности домена на контроллере домена, чтобы получить домен учетной записи компьютера или пользователя, если эта учетная запись является учетной записью в домене.

-   Если же учетная запись пользователя или компьютера является локальной учетной записью, то ее можно найти в локальной базе данных учетных записей.

## <a name="BKMK_APP"></a>Текущие приложения
Аутентификация NTLM по-прежнему поддерживается и обязательна для использования при выполнении аутентификации Windows с системами, настроенными как элемент рабочей группы. Проверка подлинности NTLM также используется для аутентификации при локальном входе на не\-контроллеров домена. Проверка подлинности Kerberos версии 5 является предпочтительным методом аутентификации для сред Active Directory, но не\-корпорацией Майкрософт или приложения могут по-прежнему использовать NTLM.

Для того чтобы сократить использование протокола NTLM в ИТ-среде, необходимо знать требования развернутых в NTLM приложений, а также стратегии и шаги, необходимые для настройки вычислительных сред, использующих другие протоколы. Добавлены новые инструменты и параметры, которые помогут вам понять принципы использования NTLM и выборочно ограничить трафик NTLM. Сведения о том, как анализировать и ограничивать использование NTLM в своих средах, см. в разделе [Вводные сведения об ограничении аутентификации NTLM](https://technet.microsoft.com/library/dd560653(v=ws.10).aspx) (руководство по аудиту и ограничению использования NTLM).

## <a name="BKMK_NEW"></a>Новые и измененные функции
Отсутствуют изменения в функциональности для NTLM для Windows Server 2012.

## <a name="BKMK_DEP"></a>Удаленные или нерекомендуемые функции
Нет не удаленные или нерекомендуемые функции NTLM для Windows Server 2012.

## <a name="BKMK_INSTALL"></a>Сведения о диспетчере сервера
NTLM нельзя использовать с диспетчером серверов. Для управления использованием проверки подлинности NTLM между компьютерными системами можно использовать параметры политики безопасности или групповые политики. В доменах протоколом проверки по умолчанию является Kerberos.

## <a name="BKMK_LINKS"></a>См. также
В следующей таблице представлены материалы по NTLM и другим технологиям проверки подлинности Windows.

|Тип содержимого|Ссылок|
|--------|-------|
|**Оценка продукта**|[Введение в ограничении аутентификации NTLM](https://technet.microsoft.com/library/dd560653.aspx)<br /><br />[Изменения в проверке подлинности NTLM](https://technet.microsoft.com/library/dd566199.aspx)|
|**Планирование**|[Руководство по моделированию угроз инфраструктуры ИТ](https://technet.microsoft.com/library/dd941826.aspx)<br /><br />[Угрозы и меры противодействия: Параметры безопасности в Windows Server 2003 и Windows XP](https://technet.microsoft.com/library/dd162275.aspx)<br /><br />[Угрозы и меры противодействия: Параметры безопасности в Windows Server 2008 и Windows Vista](https://technet.microsoft.com/library/dd349791.aspx)<br /><br />[Угрозы и меры противодействия: Параметры безопасности в Windows Server 2008 R2 и Windows 7](https://technet.microsoft.com/library/hh125921.aspx)|
|**Развертывание**|[Расширенная защита для проверки подлинности](https://support.microsoft.com/kb/968389)<br /><br />[Аудиту и ограничению руководство по использованию NTLM](https://technet.microsoft.com/library/jj865674(v=ws.10).aspx)<br /><br />[Спросите у команды разработчиков служб каталогов: Блокировка NTLM и вы: Анализ приложения методики и аудита в Windows 7](https://blogs.technet.com/askds/archive/2009/10/08/ntlm-blocking-and-you-application-analysis-and-auditing-methodologies-in-windows-7.aspx)<br /><br />[Блог, посвященный аутентификации Windows](https://blogs.technet.com/authentication/)<br /><br />[Настройка MaxConcurrentAPI для NTLM pass\-через проверку подлинности](https://social.technet.microsoft.com/wiki/contents/articles/9759.configuring-maxconcurrentapi-for-ntlm-pass-through-authentication.aspx)|
|**Разработка**|[Microsoft NTLM \(Windows\)](https://msdn.microsoft.com/library/aa378749(VS.85).aspx)<br /><br />[\[MS\-NLMP\]: NT LAN Manager \(NTLM\) спецификации протокола проверки подлинности](https://msdn.microsoft.com/library/cc236621(PROT.10).aspx)<br /><br />[\[MS\-NNTP\]: NT LAN Manager \(NTLM\) проверки подлинности: Сетевой протокол передачи новостей \(NNTP\) расширения](https://msdn.microsoft.com/library/cc236774(PROT.10).aspx)<br /><br />[\[MS\-NTHT\]: NTLM через спецификации протокола HTTP](https://msdn.microsoft.com/library/cc237488(PROT.10).aspx)|
|**Устранение неполадок**|На данный момент недоступно|
|**Ресурсы сообщества**|[Очередь недоставленных еще снова: Узкие места NTLM и среда выполнения RPC](http://blogs.technet.com/b/askds/archive/2011/09/15/is-this-horse-dead-yet-ntlm-bottlenecks-and-the-rpc-runtime.aspx)|



