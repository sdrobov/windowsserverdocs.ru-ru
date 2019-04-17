---
title: "Политики ограниченного использования программ"
description: "Безопасность Windows Server"
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: security-software-restriction-policies
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5c0befad-07c3-4262-b418-372d01850305
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/12/2016
ms.openlocfilehash: ab44013b947d33adc12c54b527415bf16c46a4c6
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="software-restriction-policies"></a>Политики ограниченного использования программ

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

В этом разделе для ИТ-специалистов, описаны политики ограниченного использования программ (SRP) в Windows Server 2012 и Windows 8 и ссылки на техническую информацию о политиках SRP начиная с Windows Server 2003.

Процедуры и советы по устранению неполадок см. в разделе [администрирование политик ограниченного использования программ](administer-software-restriction-policies.md) и [Диагностика политик ограниченного использования программ](troubleshoot-software-restriction-policies.md).

## <a name="BKMK_OVER"></a>Описание политик ограниченного использования программ
Политики ограниченного использования программ (SRP) — компонент на основе групповой политики, который идентифицирует программы, работающие на компьютерах в домене и управляет возможностью запуска этих программ. Политики ограниченного использования программ являются частью стратегии управления, позволяющей предприятиям повышать надежность, целостность и управляемость их компьютеров и безопасности Майкрософт.

Также можно использовать политики ограниченного использования программ, чтобы создать конфигурацию со строгими ограничениями для компьютеров, в которых разрешается запуск только определенных приложений. Политики ограниченного использования программ интегрируются с Microsoft Active Directory и групповой политики. Также можно создать политики ограниченного использования программ на изолированных компьютерах. Политики ограниченного использования программ являются политиками доверия, которые являются правила, устанавливаемые администратором, чтобы ограничить выполнение сценариев и другого кода, не имеющего полного доверия, запуск.

Можно определить эти политики с помощью расширения "политики ограниченного использования программ" редактор локальных групповых политик или оснастки локальной политики безопасности для Microsoft Management Console (MMC).

Подробные сведения о политиках ограниченного использования см. в разделе [Технический обзор политик ограниченного использования программ](software-restriction-policies-technical-overview.md).

## <a name="BKMK_APP"></a>Практическое применение
Администраторы могут использовать политики ограниченного использования программ для решения следующих задач:

-   Определить доверенный код

-   Разработать гибкую групповую политику для регулирования работы сценариев, исполняемых файлов и элементов управления ActiveX

Политики ограниченного использования программ применяются операционной системой и приложениями (например, сценариев), совместимые с помощью политик ограниченного использования программ.

В частности администраторы могут использовать политики ограниченного использования программ для следующих целей:

-   Укажите, какое программное обеспечение (исполняемые файлы) может выполняться на клиентах

-   Запретить пользователям выполнять определенные программы на компьютерах с общим доступом

-   Укажите, кто может добавлять доверенных издателей на клиентах

-   Установить область действия политик ограниченного использования программ (указать ли политики применяться для всех пользователей или группы пользователей на клиентах)

-   Исполняемые файлы предотвращает запуск на локальном компьютере, подразделение (OU), сайта или домена. Это уместно в случаях, когда вы не используете политик ограниченного использования программ для решения потенциальных проблем с пользователей-злоумышленников.

## <a name="BKMK_NEW"></a>Новые и измененные функции
Отсутствуют изменения в функциональных возможностях для политик ограниченного использования программ.

## <a name="BKMK_DEP"></a>Удаленные или устаревшие функции
Нет не удаленные или устаревшие функциональные возможности для политик ограниченного использования программ.

## <a name="BKMK_SOFT"></a>Требования к программному обеспечению
Расширение политик ограниченного использования программ для редактор локальных групповых политик может осуществляться через Консоль управления.

Для создания и обслуживания политик ограниченного использования программ на локальном компьютере требуются следующие компоненты:

-   Редактор локальных групповых политик

-   Установщик Windows

-   Authenticode и WinVerifyTrust

Если планируются вызовы для развертывания этих политик, в дополнение к списку выше, в домене необходимы следующие компоненты:

-   Доменные службы Active Directory

-   Групповая политика

## <a name="BKMK_INSTALL"></a>Сведения о диспетчере сервера
Политики ограниченного использования программ представляют собой расширение редактора локальной групповой политики и не устанавливаются с помощью диспетчера сервера, добавить роли и компоненты.

## <a name="BKMK_LINKS"></a>См. также:
Ниже приведены ссылки на соответствующие ресурсы для понимания и применения политик ограниченного использования Программ.

|Тип содержимого|Ссылки|
|--------|-------|
|**Период пробного использования продукта**|[Блокировка приложения с помощью политик ограниченного использования программ](https://technet.microsoft.com/magazine/2008.06.srp.aspx?pr=blog)|
|**Планирование**|[Технический обзор политик ограниченного использования программ](software-restriction-policies-technical-overview.md) (Windows Server 2012)<br /><br />[Технический справочник по политикам ограниченного использования программ](https://technet.microsoft.com/library/cc728085(v=WS.10).aspx) (Windows Server 2003)|
|**Развертывания**|Доступные ресурсы отсутствуют.|
|**Операции**|[Администрирование политик ограниченного использования программ](administer-software-restriction-policies.md) (Windows Server 2012)<br /><br />[Справка по политикам ограниченного использования программ](https://technet.microsoft.com/library/cc779607(v=WS.10).aspx) (Windows Server 2003)|
|**Устранение неполадок**|[Диагностика политик ограниченного использования программ](troubleshoot-software-restriction-policies.md) (Windows Server 2012)<br /><br />[Диагностика политик ограниченного использования программ](https://technet.microsoft.com/library/cc737011(v=WS.10).aspx) (Windows Server 2003)|
|**Безопасность**|[Угрозы и противодействия для ограниченного использования программ политик](https://technet.microsoft.com/library/dd349795(v=WS.10).aspx) (Windows Server 2008)<br /><br />[Угрозы и противодействия для ограниченного использования программ политик](https://technet.microsoft.com/library/hh125926(v=WS.10).aspx) (Windows Server 2008 R2)|
|**Средства и параметры**|[Политики ограниченного использования программ средства и параметры](https://technet.microsoft.com/library/cc782454(v=WS.10).aspx) (Windows Server 2003)|
|**Ресурсы сообщества**|[Блокировка приложения с помощью политик ограниченного использования программ](https://technet.microsoft.com/magazine/2008.06.srp.aspx?pr=blog)|


