---
title: Общие сведения о миграции удаленного доступа AlwaysOn VPN
description: AlwaysOn VPN адреса предыдущих пробелы между Windows VPN и DirectAccess и способах миграции с DirectAccess для AlwaysOn VPN.
manager: dougkim
ms.prod: windows-server
ms.technology: networking-ras
ms.topic: article
ms.assetid: eeca4cf7-90f0-485d-843c-76c5885c54b0
ms.author: pashort
author: shortpatti
ms.date: 05/29/2018
ms.openlocfilehash: 402d8ff72fe869572c9e6129cdf1aa7e755c354a
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59845985"
---
# <a name="overview-of-the-directaccess-to-always-on-vpn-migration"></a>Общие сведения о переносе DirectAccess в постоянно подключенный VPN-профиль 

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows 10

&#187; [**Next:** Планирование DirectAccess для миграции AlwaysOn VPN](da-always-on-migration-planning.md)

В предыдущих версиях Windows VPN архитектуры ограничения платформы затрудняющих ее обеспечивают критически важные функции, нуждалась в замене DirectAccess, такие как автоматического подключения, инициированные, чтобы войти в систему пользователей. AlwaysOn VPN, тем не менее, устранить большинство из этих ограничений или расширить функции VPN за пределы возможностей DirectAccess. AlwaysOn VPN адреса предыдущих пробелы между Windows VPN и DirectAccess.

DirectAccess – чтобы — Always On VPN процесс миграции состоит из четырех основных компонентов и процессов высокого уровня:


1.  **Планирование миграции AlwaysOn VPN.** Планирование помогает выявить целевых клиентов для этапа разделение пользователей, а также инфраструктуру и функциональность.

    1.  [!INCLUDE [build-migration-rings-shortdesc-include](../includes/build-migration-rings-shortdesc-include.md)]

    2.  [!INCLUDE [review-feature-mapping-shortdesc-include](../includes/review-feature-mapping-shortdesc-include.md)] 

    3.  [!INCLUDE [review-the-enhancements-shortdesc-include](../includes/review-the-enhancements-shortdesc-include.md)] 

    4.  [!INCLUDE [review-the-technology-overview-shortdesc-include](../includes/review-the-technology-overview-shortdesc-include.md)]

2.  **Развертывание инфраструктуры VPN side-by-side.** После определения вашей этапы миграции и возможности, которые вы хотите включить в развертывание, можно развернуть инфраструктуру AlwaysOn VPN параллельно с существующей инфраструктуры DirectAccess.  

3.  **Разверните сертификаты и конфигурации на клиентах.**  После подготовки инфраструктуры VPN, создания и публикации необходимые сертификаты на клиент. Когда клиенты получили сертификаты, развертывания сценария конфигурации VPN_Profile.ps1. Кроме того можно использовать Intune для настройки VPN-клиента. Использование Microsoft System Center Configuration Manager или Microsoft Intune для отслеживания успешных развертываниях конфигурации VPN.

4.  **Удаление и вывод из эксплуатации.** Списание среде после переноса всех пользователей из системы DirectAccess.

    1.  [!INCLUDE [remove-da-from-client-shortdesc-include](../includes/remove-da-from-client-shortdesc-include.md)]

    2.  [!INCLUDE [decommission-da-shortdesc-include](../includes/decommission-da-shortdesc-include.md)]


## <a name="directaccess-deployment-scenario"></a>Сценарий развертывания DirectAccess

В этом сценарии развертывания используется простой сценарий развертывания DirectAccess в качестве отправной точки для миграции, в этом руководстве представлен. Вы не обязательно должны совпадать в этом сценарии развертывания перед миграцией в AlwaysOn VPN, но для многих организаций это простая установка является точное представление текущего развертывания DirectAccess. В следующей таблице предоставляет список основных компонентов для этой установки.

Множество сценариев развертывания DirectAccess и параметров существуют, поэтому реализация может отличаться от того, описанные здесь. Если Да, см. [сопоставление функция DirectAccess и AlwaysOn VPN](../vpn/vpn-map-da.md) для определения сопоставления для добавления текущего набора функций AlwaysOn VPN, а затем добавьте эти функции в конфигурацию. Кроме того, можно ссылаться на [усовершенствования AlwaysOn VPN](../vpn/always-on-vpn/always-on-vpn-enhancements.md) можно добавить параметры развертывания AlwaysOn VPN.

>[!NOTE] 
>Для устройств, присоединенных к не входящей в домен существуют дополнительные рекомендации, такие как регистрация сертификата. Дополнительные сведения см. в разделе [AlwaysOn VPN развертывания для Windows Server и Windows 10](../vpn/always-on-vpn/deploy/always-on-vpn-deploy.md).

### <a name="deployment-scenario-feature-list"></a>Список компонентов сценария развертывания

| Функция DirectAccess | Типичный сценарий |
|-----|----|
| Сценарий развертывания                   | Развертывание DirectAccess для клиентского доступа и удаленного управления                                               |
| Сетевые адаптеры                      | 2                                                                                                              |
| Проверка подлинности пользователя                   | Учетные данные Active Directory                                                                                   |
| Использовать сертификаты компьютеров             | Да                                                                                                            |
| Группы безопасности                       | Да                                                                                                            |
| Один сервер DirectAccess            | Да                                                                                                            |
| Топология сети                      | Преобразование сетевых адресов (NAT) за пограничным брандмауэром с двумя сетевыми адаптерами                            |
| Режим доступа                           | Сквозное edge                                                                                                    |
| Туннелирование.                             | Разделенного туннелирования                                                                                                   |
| Проверка подлинности                        | Проверка подлинности инфраструктуры открытых стандартных ключей (PKI) с помощью сертификата компьютера, а также Kerberos (не KerbProxy) |
| Протоколы                             | IP-адрес по протоколу HTTPS (IP-HTTPS)                                                                                       |
| "Сети расположение сервера (NLS) off" | Да                                                                                                            |

## <a name="always-on-vpn-deployment-scenario"></a>Сценарий развертывания AlwaysOn VPN

В этом сценарии развертывания вы сосредоточиться на переход в простой среде DirectAccess на простой среде AlwaysOn VPN — это решение для замены DirectAccess. В следующей таблице приведены функции, используемые в это простое решение. Дополнительные сведения о дополнительных улучшений всегда на VPN-клиента, см. в разделе [усовершенствования AlwaysOn VPN](../vpn/always-on-vpn/always-on-vpn-enhancements.md).

### <a name="always-on-vpn-features-used-in-the-simple-environment"></a>Always On функции VPN для использования в простой среде

| VPN-функция | Сценарий конфигурации развертывания |
|-----|-----|
| Тип подключения. | Собственный протокол IKE версия 2 (IKEv2) |
| Сетевые адаптеры   | 2        |
| Проверка подлинности пользователя  | Учетные данные Active Directory            |
| Использовать сертификаты компьютеров        | Да                          |
| Маршрутизация | Разделить туннелирование |
| Разрешение имен | Список сведений о имя домена и суффикс системы доменных имен (DNS) |
| Активация | Always on» и «доверенный сетевого обнаружения |
| Проверка подлинности  | Защищенные расширяемой проверки подлинности протокол-TLS (PEAP-TLS) с помощью сертификатов пользователей — защищенный доверенным платформенным модулем |

## <a name="next-step"></a>Дальнейшие действия

[Планирование DirectAccess для миграции AlwaysOn VPN](da-always-on-migration-planning.md). Основная цель миграции — для пользователей, для обеспечения удаленного подключения к office на протяжении всего процесса.

---