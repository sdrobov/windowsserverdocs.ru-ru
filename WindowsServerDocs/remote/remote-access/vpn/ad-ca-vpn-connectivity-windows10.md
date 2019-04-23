---
title: Условный доступ для VPN-подключений с помощью Azure AD
description: На этом необязательном шаге можно точно настроить доступ авторизованных пользователей VPN ресурсы с помощью условного доступа Azure Active Directory (Azure AD).
ms.prod: windows-server-threshold
ms.technology: networking-ras
ms.topic: article
ms.assetid: ''
ms.localizationpriority: medium
ms.author: pashort
author: shortpatti
ms.date: 07/13/2018
ms.reviewer: deverette
ms.openlocfilehash: c9104a5d9ae3069e753b8b771270502c4264db96
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59885275"
---
# <a name="step-7-optional-conditional-access-for-vpn-connectivity-using-azure-ad"></a>Шаг 7. (Необязательно) Условный доступ для VPN-подключения с помощью Azure AD

&#171;  [**Предыдущих:** Шаг 6. Настройка клиента Windows 10 AlwaysOn VPN-подключений](always-on-vpn/deploy/vpn-deploy-client-vpn-connections.md)<br>
&#187; [ **Next:** Шаг 7.1. Настроить EAP-TLS, чтобы пропустить проверку списка отзыва сертификатов (CRL)](vpn-config-eap-tls-to-ignore-crl-checking.md)

На этом необязательном шаге можно точно настроить как VPN пользователи доступ к ресурсам с помощью [условного доступа Azure Active Directory (Azure AD)](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). С помощью условного доступа Azure AD для подключения к виртуальной частной сети (VPN) можно защитить VPN-подключений. Условный доступ — это модуль оценки на основе политик, который позволяет создавать правила доступа для любого приложения, подключенного к Azure Active Directory (Azure AD). 

## <a name="prerequisites"></a>предварительные требования

Вы знакомы со следующими статьями:
- [Условный доступ в Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [VPN и условный доступ](https://docs.microsoft.com/windows/access-protection/vpn/vpn-conditional-access)

Чтобы настроить условный доступ Azure Active Directory для VPN-подключения, необходимо иметь следующие условия:
- [Инфраструктура сервера](always-on-vpn/deploy/vpn-deploy-server-infrastructure.md)
- [Сервер удаленного доступа для Always On VPN](always-on-vpn/deploy/vpn-deploy-ras.md)
- [Сервер политики сети](always-on-vpn/deploy/vpn-deploy-nps.md)
- [DNS и параметров брандмауэра](always-on-vpn/deploy/vpn-deploy-dns-firewall.md)
- [Windows 10 клиент всегда подключен к VPN-подключений](always-on-vpn/deploy/vpn-deploy-client-vpn-connections.md)

## <a name="step-71-configure-eap-tls-to-ignore-certificate-revocation-list-crl-checkingvpn-config-eap-tls-to-ignore-crl-checkingmd"></a>[Шаг 7.1. Настроить EAP-TLS, чтобы пропустить проверку списка отзыва сертификатов (CRL)](vpn-config-eap-tls-to-ignore-crl-checking.md)

На этом этапе можно добавить **IgnoreNoRevocationCheck** и настройте его для разрешения проверки подлинности клиентов в том случае, если сертификат не содержит точки распространения списков отзыва Сертификатов. По умолчанию IgnoreNoRevocationCheck имеет значение 0 (отключен).

Клиент EAP-TLS не удается подключиться, если сервер политики сети завершается проверка цепочки сертификатов (включая корневой сертификат). Cloud сертификаты, выданные Azure AD для пользователя нет список отзыва Сертификатов, поскольку они являются короткоживущими сертификаты со сроком жизни один час. EAP на сервере политики сети должен быть настроен для игнорирования отсутствие списка отзыва Сертификатов. Так как метод проверки подлинности EAP-TLS, это значение реестра необходим только в разделе **EAP\13**. Если используются другие методы проверки подлинности EAP, затем значение реестра необходимо добавить в те также. 




## <a name="step-72-create-root-certificates-for-vpn-authentication-with-azure-advpn-create-root-cert-for-vpn-auth-azure-admd"></a>[Шаг 7.2. Создать корневые сертификаты для проверки подлинности VPN с Azure AD](vpn-create-root-cert-for-vpn-auth-azure-ad.md)

На этом шаге настраивается корневые сертификаты для проверки подлинности VPN с Azure AD, который автоматически создает VPN server облачного приложения в клиенте.  

Чтобы настроить условный доступ для VPN-подключения, вам потребуется:
1. Создание VPN-сертификат на портале Azure (можно создать несколько сертификатов).
2. Скачайте VPN-сертификат.
3. Разверните сертификат на VPN-сервере.

## <a name="step-73-configure-the-conditional-access-policyvpn-config-conditional-access-policymd"></a>[Шаг 7.3. Настройка политики условного доступа](vpn-config-conditional-access-policy.md)

На этом шаге настройкой политики условного доступа для VPN-подключения. 

Чтобы настроить политики условного доступа, вам потребуется:
1. Создание политики условного доступа, назначенный для пользователей VPN.
2. Значение в Облачное приложение **VPN-сервер**.
3. Grant (управления доступом) присвоено **требовать многофакторную проверку подлинности**.  При необходимости можно использовать другие элементы управления.

## <a name="step-74-deploy-conditional-access-root-certificates-to-on-premises-advpn-deploy-cond-access-root-cert-to-on-premise-admd"></a>[Шаг 7.4. Развертывание сертификатов корневого условного доступа к локальным AD](vpn-deploy-cond-access-root-cert-to-on-premise-ad.md)

На этом этапе развертывании доверенный корневой сертификат для проверки подлинности VPN в локальной AD.

Чтобы развернуть доверенный корневой сертификат, вам потребуется:
1. Добавьте Скачанный сертификат в виде *доверенного корневого ЦС для проверки подлинности VPN*.
2. Импортируйте корневой сертификат VPN-сервера и VPN-клиента.
3. Убедитесь, что сертификаты присутствуют и Показать как доверенные.


## <a name="step-75-create-oma-dm-based-vpnv2-profiles-to-windows-10-devicesvpn-create-oma-dm-based-vpnv2-profilesmd"></a>[Шаг 7.5. Создание OMA-DM на основе VPNv2 профилей на устройствах Windows 10](vpn-create-oma-dm-based-vpnv2-profiles.md)

На этом этапе можно создать OMA-DM на основе профилей VPNv2, с помощью Intune для развертывания политики конфигурации VPN-устройства. Если вы хотите использовать SCCM или скрипт PowerShell для создания профилей VPNv2, см. в разделе [VPNv2 CSP параметры](https://docs.microsoft.com/windows/client-management/mdm/vpnv2-csp) для получения дополнительных сведений. 


## <a name="next-step"></a>Дальнейшие действия
[Шаг 7.1. Настроить EAP-TLS, чтобы пропустить проверку списка отзыва сертификатов (CRL)](vpn-config-eap-tls-to-ignore-crl-checking.md): На этом шаге необходимо добавить **IgnoreNoRevocationCheck** и настройте его для разрешения проверки подлинности клиентов в том случае, если сертификат не содержит точки распространения списков отзыва Сертификатов. По умолчанию IgnoreNoRevocationCheck имеет значение 0 (отключен).

---

## <a name="related-topics"></a>См. также
- [Настройка профилей VPNv2](https://docs.microsoft.com/windows/access-protection/vpn/vpn-conditional-access): VPN-клиент теперь может интегрироваться с облачной платформой условного доступа для соблюдения требований при использовании удаленных клиентов. На этом шаге необходимо настроить профили VPNv2 с  **\<DeviceCompliance > \<включено > значение true,\<и включения >**. 
 
- [Усовершенствование удаленного доступа в Windows 10 с профилем VPN автоматического](https://www.microsoft.com/itshowcase/Article/Content/894/Enhancing-remote-access-in-Windows-10-with-an-automatic-VPN-profile): Узнайте, как корпорация Майкрософт реализовала условного доступа для VPN-подключения. Профили VPN содержат все сведения, необходимые устройства для подключения к корпоративной сети, включая методы проверки подлинности, которые поддерживаются и VPN-сервер, на которой должны подключаться устройства. Изменения в юбилейном обновлении Windows 10, включая условный доступ и единый вход, дали нам для создания профиля подключения VPN с использованием AlwaysOn. Мы создали профиль подключения для присоединенных к домену и устройств, управляемых Intune Microsoft, с помощью консоли System Center Configuration Manager. 

- [Условный доступ в Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal): Безопасность очень важна для организаций, использующих облако. Ключевым аспектом облачной безопасности является идентификация и доступ, когда дело доходит до управления облачными ресурсами. В мире мобильных и облачных пользователей к ресурсам организации с помощью различных устройств и приложений из любого места. Как следствие этого просто указать, кто имеет доступ к ресурсу уже недостаточно. Чтобы балансом между безопасностью и производительностью, ИТ-специалисты также должны учитывать как ресурса при одновременном в решении по управлению управления доступом.

- [VPN и условный доступ](https://docs.microsoft.com/windows/access-protection/vpn/vpn-conditional-access): VPN-клиент теперь может интегрироваться с облачной платформой условного доступа для соблюдения требований при использовании удаленных клиентов. Условный доступ — это модуль оценки на основе политик, который позволяет создавать правила доступа для любого приложения, подключенного к Azure Active Directory (Azure AD). 

---