---
title: Настройка игнорирования проверки списка отзыва сертификатов (CRL) в EAP-TLS
description: Протокол EAP-TLS клиент не может подключиться, пока завершает проверку отзыва цепочку сертификатов (включая корневой сертификат) клиента и позволяет убедиться, что отозванных сертификатов сервера политики сети.
services: active-directory
ms.prod: windows-server-threshold
ms.technology: networking-ras
documentationcenter: ''
ms.assetid: ''
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 07/13/2018
ms.author: pashort
author: shortpatti
ms.localizationpriority: medium
ms.reviewer: deverette
ms.openlocfilehash: ac59c554c69a6138a106a648c3fab3ed4fe05b7b
ms.sourcegitcommit: 4893d79345cea85db427224bb106fc1bf88ffdbc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2018
ms.locfileid: "6067510"
---
# Шаг 7.1. Настройка игнорирования проверки списка отзыва сертификатов (CRL) в EAP-TLS

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows 10

& #171;  [ **Предыдущих:** шаг 7. (Необязательно) Условный доступ для подключения к VPN с помощью Azure AD](ad-ca-vpn-connectivity-windows10.md)<br>
& #187; [ **Далее:** шаг 7.2. Создание корневые сертификаты для проверки подлинности VPN с Azure AD](vpn-create-root-cert-for-vpn-auth-azure-ad.md)

>[!IMPORTANT]
>Сбой реализовать это изменение реестра приведет к подключений IKEv2, использование облачных сертификатов с помощью протокола PEAP может завершиться сбоем, но подключений IKEv2, с помощью Client Auth сертификаты, выданные локального центра сертификации будет продолжать работать.

На этом этапе можно добавить **IgnoreNoRevocationCheck** и установите для него разрешить проверки подлинности клиентов, когда сертификат не содержит точки распространения списков ОТЗЫВА. По умолчанию IgnoreNoRevocationCheck имеет значение 0 (отключено).

>[!NOTE]
>Если маршрутизацию Windows и сервера удаленного доступа (RRAS) использует NPS для прокси-сервера RADIUS вызывает на второй сервер политики сети, а затем необходимо задать **IgnoreNoRevocationCheck = 1** на обоих серверах.

Протокол EAP-TLS клиент не может подключиться, если сервера политики сети завершает проверку отзыва цепочке сертификатов (включая корневой сертификат). Облако сертификаты, выданные Azure AD для пользователя не имеют списка отзыва Сертификатов, так как они являются кратковременные сертификаты с жизненным циклом один час. Протокол EAP в NPS необходимо настроить игнорирование отсутствие списка отзыва Сертификатов. По умолчанию IgnoreNoRevocationCheck имеет значение 0 (отключено). Добавление IgnoreNoRevocationCheck и присвойте ему значение 1, чтобы разрешить проверки подлинности клиентов, когда сертификат не содержит точки распространения списков ОТЗЫВА. 

Так как метод проверки подлинности EAP-TLS, это значение реестра требуется только в разделе EAP\13. Если используются другие методы проверки подлинности EAP, затем значение реестра следует добавить в них также. 

**Процедура**

1. Откройте **regedit.exe** на сервер политики сети.

2. Перейдите к **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\RasMan\PPP\EAP\13**.

3. Щелкните **Изменить > создать** выберите **параметр типа DWORD (32-разрядная версия)** и введите **IgnoreNoRevocationCheck**.

4. Дважды щелкните **IgnoreNoRevocationCheck** и установить значение **1**.

5. Нажмите кнопку **ОК** и перезагрузите сервер. Перезапуск службы RRAS и NPS недостаточно.

Дополнительные сведения см. в разделе [Включение или отключение проверка отзыва сертификатов (CRL) на клиентских компьютерах](https://technet.microsoft.com/library/bb680540.aspx).


|Путь реестра  |Расширение EAP  |
|---------|---------|
|HKLM\SYSTEM\CurrentControlSet\Services\RasMan\PPP\EAP\13     |EAP-TLS         |
|HKLM\SYSTEM\CurrentControlSet\Services\RasMan\PPP\EAP\25     |ПРОТОКОЛ PEAP         |
|HKLM\SYSTEM\CurrentControlSet\Services\RasMan\PPP\EAP\26     |Протокол EAP-MSCHAP версии 2         |

## Дальнейшие действия

Шаг [7.2. Создание корневые сертификаты для проверки подлинности VPN с Azure AD](vpn-create-root-cert-for-vpn-auth-azure-ad.md): на этом этапе Настройка условного доступа корневые сертификаты для проверки подлинности VPN с помощью Azure AD, который автоматически создает VPN-сервера облачных приложений в клиенте. 

---