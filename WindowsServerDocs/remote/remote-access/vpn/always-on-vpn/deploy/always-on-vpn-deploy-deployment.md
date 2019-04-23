---
title: Развертывание постоянно подключенного VPN-профиля
description: В этом разделе приведены подробные инструкции по развертыванию AlwaysOn VPN в Windows Server 2016.
ms.prod: windows-server-threshold
ms.technology: networking-ras
ms.topic: article
ms.assetid: ad748de2-d175-47bf-b05f-707dc48692cf
ms.localizationpriority: medium
ms.date: 11/05/2018
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 15c60f2986d3837c5c6e03f9e0a25c7e0a4e0cc0
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59867145"
---
# <a name="deploy-always-on-vpn"></a>Развертывание постоянно подключенного VPN-профиля

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows 10

&#0171;[ **Предыдущих:** Дополнительные сведения о AlwaysOn VPN дополнительные функции](always-on-vpn-adv-options.md)<br>
&#0187; [ **Next:** Шаг 1. Начать планирование развертывания AlwaysOn VPN](always-on-vpn-deploy-planning.md)

В этом разделе вы узнаете о рабочий процесс для развертывания всегда на VPN-подключения для удаленного присоединенных к домену Windows 10 клиентских компьютеров. Если вы хотите **настроить условный доступ** для тонкой настройки, как пользователи VPN-доступ к ресурсам, см. в разделе [условного доступа для VPN-подключения с помощью Azure AD](../../ad-ca-vpn-connectivity-windows10.md). Дополнительные сведения об условном доступе для VPN-подключения с помощью Azure AD, см. в разделе [условного доступа в Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). 


На схеме ниже рабочий процесс для различных сценариев при развертывании AlwaysOn VPN: 

_Щелкните изображение, чтобы увеличить_.

<a href="../../../../media/Always-On-Vpn/always-on-vpn-deployment-workflow.png" alt="Full-sized view of the Always On VPN deployment workflow" target="_blank">![Эскиз](../../../../media/Always-On-Vpn/always-on-vpn-deployment-workflow-sm.png)
</a> 

>[!IMPORTANT]
>Для этого развертывания это не является обязательным, выполнение серверов инфраструктуры, например компьютеров под управлением доменных служб Active Directory, службы сертификатов Active Directory и сервера политики сети, Windows Server 2016. Более ранних версиях Windows Server, например Windows Server 2012 R2, можно использовать для серверов инфраструктуры, так и для сервера, на котором работает удаленный доступ.

## <a name="step-1-plan-the-always-on-vpn-deploymentalways-on-vpn-deploy-planningmd"></a>[Шаг 1. Планирование развертывания VPN Always On](always-on-vpn-deploy-planning.md)

На этом шаге вы начать планирование и Подготовка развертывания AlwaysOn VPN. Перед установкой роли сервера удаленного доступа на компьютере, который вы планируете использование в качестве VPN-сервера. После правильного планирования, можно развернуть AlwaysOn VPN и при необходимости настроить условный доступ для VPN-подключения с помощью Azure AD.

## <a name="step-2-configure-the-always-on-vpn-server-infrastructurevpn-deploy-server-infrastructuremd"></a>[Шаг 2. Настройка Always On Server инфраструктуры VPN](vpn-deploy-server-infrastructure.md)

На этом шаге вы установите и настройте серверные компоненты, необходимые для поддержки VPN-Подключение. Серверные компоненты включают настройке PKI для распространения сертификатов, которые используются пользователями, VPN-сервер и сервер политики сети.  Можно также настроить RRAS для поддержки подключения IKEv2 и NPS-сервере для выполнения авторизации для VPN-подключений.

Настройка инфраструктуры сервера, необходимо выполнить следующие задачи:
- **На сервере, настроенном с доменными службами Active Directory:** Включение автоматической регистрации сертификатов в групповой политике для компьютеров и пользователей, создайте группу пользователей VPN, в группу серверов VPN и группы серверов политики сети и добавление членов в каждой группе.
- **На сервере Active Directory сертификат ЦС:** Создание шаблонов сертификатов проверки подлинности пользователя, проверки подлинности сервера VPN и проверки подлинности сервера политики сети.
- **На присоединенных к домену клиенты Windows 10.** Регистрации и проверки сертификатов пользователя.

## <a name="step-3-configure-the-remote-access-server-for-always-on-vpnvpn-deploy-rasmd"></a>[Шаг 3. Настройка сервера удаленного доступа для AlwaysOn для VPN-ШЛЮЗА](vpn-deploy-ras.md)

На этом этапе Настройка удаленного доступа VPN, чтобы разрешить VPN-подключения IKEv2, запретить подключения из других протоколов VPN и назначить пулу статических IP-адресов для выдачи IP-адресов в подключение авторизованных клиентов VPN.

Для настройки удаленного доступа, необходимо выполнить следующие задачи:
- Зарегистрировать и проверить сертификат сервера VPN
- Установка и настройка удаленного доступа VPN

## <a name="step-4-install-and-configure-the-nps-servervpn-deploy-npsmd"></a>[Шаг 4. Установка и настройка сервера политики сети](vpn-deploy-nps.md)

На этом шаге с помощью Windows PowerShell или Server Manager Добавить роли и функции мастера установки сервера политики сети (NPS). Можно также настроить NPS так, чтобы обрабатывать все проверки подлинности, авторизации и учета обязанностей для запроса на подключение, которое поступает от VPN-сервера.

Чтобы настроить сервер политики сети, необходимо выполнить следующие задачи:
- Регистрация сервера политики сети в Active Directory
- Настройка RADIUS учета для сервера политики сети
- Добавить VPN-сервера в качестве клиента RADIUS на сервере политики сети
- Настройка политики сети на сервере политики сети
- Автоматическая регистрация сертификата сервера политики сети

## <a name="step-5-configure-dns-and-firewall-settings-for-always-on-vpnvpn-deploy-dns-firewallmd"></a>[Шаг 5. Настройка DNS и параметрами брандмауэра для AlwaysOn для VPN-ШЛЮЗА](vpn-deploy-dns-firewall.md)

На этом шаге вы настроите DNS и брандмауэра параметры. При подключении VPN-клиентам, они используют же DNS-серверы, используемые вашей внутренних клиентов, что позволяет им для разрешения имен в так же, как остальная часть внутреннего рабочие станции. 

## <a name="step-6-configure-windows-10-client-always-on-vpn-connectionsvpn-deploy-client-vpn-connectionsmd"></a>[Шаг 6. Настройка клиента Windows 10 AlwaysOn VPN-подключений](vpn-deploy-client-vpn-connections.md)

На этом шаге Настройте клиентские компьютеры Windows 10 для взаимодействия с этой инфраструктурой с помощью VPN-подключения. Можно использовать несколько технологий для настройки VPN для Windows 10 клиентов, включая Windows PowerShell, System Center Configuration Manager и Intune. Все три требуется профиль VPN в формате XML, чтобы настроить соответствующие параметры VPN. 

## <a name="step-7-optional-configure-conditional-access-for-vpn-connectivityad-ca-vpn-connectivity-windows10md"></a>[Шаг 7. (Необязательно) Настройка условного доступа для VPN-подключения](../../ad-ca-vpn-connectivity-windows10.md) 
На этом необязательном шаге можно точно настроить VPN авторизованных пользователей доступа к ресурсам. С помощью условного доступа Azure AD для VPN-подключения можно защитить VPN-подключений. Условный доступ — механизм оценки на основе политик, который позволяет создавать правила доступа для Azure AD подключения приложения. Дополнительные сведения см. в разделе [условного доступа Azure Active Directory (Azure AD)](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).


## <a name="next-step"></a>Дальнейшие действия
[Шаг 1. Планирование развертывания AlwaysOn VPN](always-on-vpn-deploy-planning.md): Перед установкой роли сервера удаленного доступа на компьютере, который вы планируете использование в качестве VPN-сервера. После правильного планирования, можно развернуть AlwaysOn VPN и при необходимости настроить условный доступ для VPN-подключения с помощью Azure AD.  



---