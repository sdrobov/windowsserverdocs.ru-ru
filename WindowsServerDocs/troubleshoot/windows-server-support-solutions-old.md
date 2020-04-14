---
title: Основные решения поддержки для Windows Server
description: Получите ссылки на решения для проблем с Windows Server
ms.prod: windows-server
manager: alant
ms.technology: server-general
ms.date: 03/16/2018
ms.topic: article
author: kaushika-msft
ms.author: elizapo
ms.openlocfilehash: 6bd0d22c7df7344e6c4bfbf8360532ab0f36d117
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80820757"
---
# <a name="top-support-solutions-for-windows-server-2016"></a>Основные решения поддержки для Windows Server 2016

Корпорация Майкрософт регулярно выпускает обновления и решения для Windows Server. Необходимо вовремя обновлять серверы, чтобы они могли получать будущие обновления, в том числе обновления безопасности. Полный список выпущенных обновлений см. в разделе [Журнал обновлений Windows 10 и Windows Server 2016](https://support.microsoft.com/help/4000825/windows-10-windows-server-2016-update-history).

Это лучшие решения службы поддержки Майкрософт для наиболее распространенных проблем при использовании Windows Server 2016. Ниже представлены ссылки на статьи базы знаний и библиотеки, а также на обновления.

>[!TIP]
> Ищете дополнительные сведения о старых версиях Windows Server? Ознакомьтесь с другими нашими [библиотеками Windows Server](/previous-versions/windows/) на сайте docs.microsoft.com. Кроме того, вы можете найти нужную информацию [на этом сайте](https://docs.microsoft.com/search/index?search=Windows+Server&dataSource=previousVersions).

## <a name="solutions-for-installing-or-upgrading-windows-server"></a>Решения для установки или обновления Windows Server

- [Устранение ошибок обновления Windows 10: технические сведения для ИТ-специалистов](https://docs.microsoft.com/windows/deployment/upgrade/resolve-windows-10-upgrade-errors)
- [Обновление стека обслуживания для Windows 10 версии 1607 и Windows Server 2016:8 августа 2017](https://support.microsoft.com/help/4035631)
- [Обновление совместимости для обновления до Windows 10 версии 1607 и Windows Server 2016:3 августа 2017](https://support.microsoft.com/help/4033524)
- [Обновление системы на месте не поддерживается на виртуальных машинах Azure под управлением Windows.](https://support.microsoft.com/help/4014997)
- [Варианты обновления и преобразования для Windows Server 2016](../get-started/supported-upgrade-paths.md)
- [Матрица обновления ролей сервера и миграции для Windows Server 2016](../get-started/server-role-upgradeability-table.md)
- [Установка и обновление Windows Server](../get-started/installation-and-upgrade.md)
- [Заметки о выпуске: важные проблемы в Windows Server 2016](../get-started/windows-server-2016-ga-release-notes.md)
- [Рекомендации по переходу на Windows Server 2016](../get-started/recommendations-moving-to-server2016.md)

## <a name="solutions-for-volume-activation"></a>Решения для активации корпоративных лицензий
- [Активация Windows Server 2016](../get-started/server-2016-activation.md)
- [Проверка и выбор методов активации](https://technet.microsoft.com/library/jj134256(ws.11).aspx)
- [Коды ошибок активации для многопользовательской активации](https://technet.microsoft.com/library/dn502528.aspx)
- [Устранение неполадок службы управления ключами (KMS)](https://technet.microsoft.com/library/ee939272.aspx)
- [Устранение неполадок многопользовательской активации](https://technet.microsoft.com/library/ff793439.aspx)
- [Коды ошибок активации](https://technet.microsoft.com/library/ff793399.aspx)
- [Установка Windows может завершиться с ошибкой "указанный ключ продукта не соответствует ни одному из образов Windows, доступных для установки. Введите другой ключ продукта "](https://support.microsoft.com/help/2796988/windows-8-or-windows-server-2012-installation-may-fail-with-error-mess)

## <a name="solutions-related-to-dcpromo-and-installing-domain-controllers"></a>Решения, связанные с DCPromo и установкой контроллера домена
- [Требования к портам Active Directory и домен Active Directory Services](https://technet.microsoft.com/library/dd772723(v=ws.10).aspx)
- [Active Directory порты брандмауэра — Давайте попробуем сделать это простым](http://blogs.msmvps.com/acefekay/2011/11/01/active-directory-firewall-ports-let-s-try-to-make-this-simple/)
- [Поддержка Exchange Server для Windows Server 2016](https://technet.microsoft.com/library/ff728623(v=exchg.150).aspx)
- [Использование программы Ntdsutil. exe для перемещения или захвата ролей FSMO контроллеру домена](https://support.microsoft.com/kb/255504)
- [Устранение неполадок с развертыванием контроллера домена](../identity/ad-ds/deploy/troubleshooting-domain-controller-deployment.md)
- [Устранение неполадок мастера установки Active Directory](https://msdn.microsoft.com/library/bb727058.aspx)
- [Известные проблемы при установке и удалении AD DS](https://technet.microsoft.com/library/cc754463(v=ws.10).aspx)

## <a name="solutions-for-active-directory-federation-services-ad-fs"></a>Решения для служб федерации Active Directory (AD FS)
- [Настройка автоматической регистрации присоединенных к домену устройств Windows с помощью Azure Active Directory](/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup)
- [Настройка выдачи утверждений](/azure/active-directory/device-management-hybrid-azuread-joined-devices-setup#step-2-setup-issuance-of-claims)
- [Настройка AD FS для аутентификации пользователей, хранящихся в каталогах LDAP](../identity/ad-fs/operations/configure-ad-fs-to-authenticate-users-stored-in-ldap-directories.md)
- [Поддержка привязки альтернативного имени узла для аутентификации сертификата в AD FS](../identity/ad-fs/operations/ad-fs-support-for-alternate-hostname-binding-for-certificate-authentication.md)
- [Защита от атак с использованием пароля](https://blogs.technet.microsoft.com/tspring/2017/01/20/federated-to-microsoft-cloud-and-account-lockouts/)
- [Обновление до AD FS в Windows Server 2016 с помощью базы данных WID](../identity/ad-fs/deployment/upgrading-to-ad-fs-in-windows-server-2016.md)
- [Вход в Windows 10 — Включение проверки подлинности устройства с помощью AD FS](../identity/ad-fs/operations/configure-device-based-conditional-access-on-premises.md)
- [Управление SSL-сертификатами в AD FS и WAP в Windows Server 2016](../identity/ad-fs/operations/manage-ssl-certificates-ad-fs-wap-2016.md)
- [Политики управления доступом в Windows Server 2016 AD FS](../identity/ad-fs/operations/access-control-policies-in-ad-fs.md)

## <a name="solutions-related-to-active-directory-replication"></a>Решения, связанные с репликацией Active Directory

- [Устранение неполадок с репликацией Active Directory](../identity/ad-ds/manage/troubleshoot/troubleshooting-active-directory-replication-problems.md)
- [Загрузка Состояние репликации Active Directory средства из центра загрузки Майкрософт](https://www.microsoft.com/en-in/download/details.aspx?id=30005)
- [E2E. Устранение распространенных ошибок репликации Active Directory](https://support.microsoft.com/kb/3108513)
- [Устранение ошибки репликации Active Directory 8606: недостаточно атрибутов для создания объекта](https://support.microsoft.com/kb/2028495)
- [События с ИДЕНТИФИКАТОРом 2108 и 1084 происходят во время входящей репликации Active Directory в Windows 2000 Server и в Windows Server 2003](https://support.microsoft.com/kb/837932)
- [Устранение ошибки репликации Active Directory 8451: при выполнении операции репликации произошла ошибка базы данных](https://support.microsoft.com/kb/2645996)
- [Устранение ошибки репликации Active Directory 1127: во время доступа к жесткому диску операция с диском завершилась сбоем даже после повторных попыток](https://support.microsoft.com/kb/2025726)
- [Очистка метаданных сервера](https://technet.microsoft.com/library/cc816907.aspx)