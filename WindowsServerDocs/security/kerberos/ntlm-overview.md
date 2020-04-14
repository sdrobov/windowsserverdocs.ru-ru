---
title: Обзор протокола NTLM
description: Безопасность Windows Server
ms.prod: windows-server
ms.technology: security-kerberos
ms.topic: article
ms.assetid: 773909fd-c0bc-498a-95fc-bb452ec04d90
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/12/2016
ms.openlocfilehash: 250b1e7e0fc3a49fc261c70673a5ad6aa15c97b0
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80858857"
---
# <a name="ntlm-overview"></a>Обзор протокола NTLM

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

В этой статье для ИТ Professional описывается NTLM, любые изменения в работе и предоставляются ссылки на технические ресурсы по проверке подлинности Windows и NTLM для Windows Server 2012 и предыдущих версий.

## <a name="feature-description"></a><a name="BKMK_OVER"></a> Описание функции
Проверка подлинности NTLM — это семейство протоколов проверки подлинности, которые входят в состав Windows Msv1\_0. dll. Протоколы проверки подлинности NTLM включают LAN Manager версий 1 и 2, а также NTLM версий 1 и 2. Протоколы проверки подлинности NTLM выполняют проверку подлинности пользователей и компьютеров на основе запроса\/механизм ответа, который доказывает серверу или контроллеру домена о том, что пользователь знает пароль, связанный с учетной записью. При использовании протокола NTLM сервер ресурсов должен выполнять одно из следующих действий для проверки удостоверения пользователя или компьютера каждый раз, как возникает необходимость в новом маркере доступа:

-   Свяжитесь со службой проверки подлинности домена на контроллере домена, чтобы получить домен учетной записи компьютера или пользователя, если эта учетная запись является учетной записью в домене.

-   Если же учетная запись пользователя или компьютера является локальной учетной записью, то ее можно найти в локальной базе данных учетных записей.

## <a name="current-applications"></a><a name="BKMK_APP"></a>Текущие приложения
Аутентификация NTLM по-прежнему поддерживается и обязательна для использования при выполнении аутентификации Windows с системами, настроенными как элемент рабочей группы. Проверка подлинности NTLM также используется для проверки подлинности локального входа на контроллеры домена, не\-. Проверка подлинности Kerberos версии 5 является предпочтительным методом проверки подлинности для Active Directory сред, но не\-приложения Майкрософт или Майкрософт могут по-прежнему использовать NTLM.

Для того чтобы сократить использование протокола NTLM в ИТ-среде, необходимо знать требования развернутых в NTLM приложений, а также стратегии и шаги, необходимые для настройки вычислительных сред, использующих другие протоколы. Добавлены новые инструменты и параметры, которые помогут вам понять принципы использования NTLM и выборочно ограничить трафик NTLM. Сведения о том, как анализировать и ограничивать использование NTLM в своих средах, см. в разделе [Вводные сведения об ограничении аутентификации NTLM](https://technet.microsoft.com/library/dd560653(v=ws.10).aspx) (руководство по аудиту и ограничению использования NTLM).

## <a name="new-and-changed-functionality"></a><a name="BKMK_NEW"></a>Новые и измененные функции
Нет изменений в функциональности NTLM для Windows Server 2012.

## <a name="removed-or-deprecated-functionality"></a><a name="BKMK_DEP"></a>Удаленная или устаревшая функциональность
Отсутствует удаленная или устаревшая функциональность для NTLM для Windows Server 2012.

## <a name="server-manager-information"></a><a name="BKMK_INSTALL"></a>Сведения о диспетчер сервера
NTLM нельзя использовать с диспетчером серверов. Для управления использованием проверки подлинности NTLM между компьютерными системами можно использовать параметры политики безопасности или групповые политики. В доменах протоколом проверки по умолчанию является Kerberos.

## <a name="see-also"></a><a name="BKMK_LINKS"></a> См. также
В следующей таблице представлены материалы по NTLM и другим технологиям проверки подлинности Windows.

|Тип контента|Ссылки|
|--------|-------|
|**Оценка продукта**|[Введение в ограничение проверки подлинности NTLM](https://technet.microsoft.com/library/dd560653.aspx)<p>[Изменения в проверке подлинности NTLM](https://technet.microsoft.com/library/dd566199.aspx)|
|**Планирование**|[Путеводитель по моделированию угроз для ИТ – инфраструктуры](https://technet.microsoft.com/library/dd941826.aspx)<p>[Угрозы и контрмеры: параметры безопасности в Windows Server 2003 и Windows XP](https://technet.microsoft.com/library/dd162275.aspx)<p>[Руководство по угрозам и контрмерам: параметры безопасности в Windows Server 2008 и Windows Vista](https://technet.microsoft.com/library/dd349791.aspx)<p>[Руководство по угрозам и контрмерам: параметры безопасности в Windows Server 2008 R2 и Windows 7](https://technet.microsoft.com/library/hh125921.aspx)|
|**Развертывание**|[расширенная защита для проверки подлинности](https://support.microsoft.com/kb/968389)<p>[Аудит и запрещение рекомендаций по использованию NTLM](https://technet.microsoft.com/library/jj865674(v=ws.10).aspx)<p>[Обратитесь к группе служб каталогов: Блокировка NTLM и вы: методы анализа и аудита приложений в Windows 7](https://blogs.technet.com/askds/archive/2009/10/08/ntlm-blocking-and-you-application-analysis-and-auditing-methodologies-in-windows-7.aspx)<p>[Блог о проверке подлинности Windows](https://blogs.technet.com/authentication/)<p>[Настройка MaxConcurrentAPI для передачи\-NTLM с помощью проверки подлинности](https://social.technet.microsoft.com/wiki/contents/articles/9759.configuring-maxconcurrentapi-for-ntlm-pass-through-authentication.aspx)|
|**Разработчик**|[Microsoft NTLM \(Windows\)](https://msdn.microsoft.com/library/aa378749(VS.85).aspx)<p>[\[MS\-НЛМП\]: NT LAN Manager \(NTLM\) спецификация протокола проверки подлинности](https://msdn.microsoft.com/library/cc236621(PROT.10).aspx)<p>[\[MS\-NNTP\]: NT LAN Manager \(NTLM\) Authentication: протокол сетевого обмена новостей \(расширение NNTP\)](https://msdn.microsoft.com/library/cc236774(PROT.10).aspx)<p>[\[MS\-НСТ\]: Спецификация протокола NTLM по протоколу HTTP](https://msdn.microsoft.com/library/cc237488(PROT.10).aspx)|
|**Устранение неполадок**|На данный момент недоступно|
|**Ресурсы сообщества**|[Эта лошадиная работа еще не завершена: узкие места NTLM и среда выполнения RPC](https://blogs.technet.com/b/askds/archive/2011/09/15/is-this-horse-dead-yet-ntlm-bottlenecks-and-the-rpc-runtime.aspx)|



