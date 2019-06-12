---
title: Виртуальная частная сеть (VPN)
description: Дополнительные сведения о Windows Server 2016 и VPN для Windows 10 функции и возможности, можно использовать в этом разделе.
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: cd4908f0-0d6f-4c02-8f98-4dc88c3dcb65
ms.date: 11/05/2018
ms.author: pashort
author: shortpatti
ms.localizationpriority: medium
ms.openlocfilehash: bfd00b7a13e9fad113da1191e7ccd33965223070
ms.sourcegitcommit: 0948a1abff1c1be506216eeb51ffc6f752a9fe7e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2019
ms.locfileid: "66749559"
---
# <a name="virtual-private-networking-vpn"></a>Виртуальная частная сеть (VPN)

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows 10

## <a name="ras-gateway-as-a-single-tenant-vpn-server"></a>Шлюз RAS как один клиент VPN-сервера

В Windows Server 2016 роль сервера удаленного доступа — это логическая группа следующих технологий сетевого доступа.

- Служба удаленного доступа (RAS)
- Маршрутизация
- Прокси-сервер веб-приложения

Эти технологии являются службы ролей, роли сервера удаленного доступа.

При установке роли сервера удаленного доступа с помощью мастера добавления ролей и компонентов или Windows PowerShell, можно установить один или несколько из этих трех ролей служб.

При установке **DirectAccess и VPN (RAS)** службы роли, при развертывании шлюза службы удаленного доступа (**шлюза RAS**). Вы можете развернуть шлюз RAS, как сервер виртуальной частной сети (VPN) шлюза RAS одного клиента, который предоставляет многие дополнительные функции и улучшенные возможности.

>[!NOTE]
>Также можно развернуть шлюз RAS качестве Мультитенантного VPN-сервера для использования с программно определяемой сети (SDN), или как сервер DirectAccess. Дополнительные сведения см. в разделе [шлюза RAS](https://docs.microsoft.com/windows-server/remote/remote-access/ras-gateway/ras-gateway), [программно определяемой сети (SDN)](https://docs.microsoft.com/windows-server/networking/sdn/software-defined-networking), и [DirectAccess](https://docs.microsoft.com/windows-server/remote/remote-access/directaccess/directaccess).

## <a name="related-topics"></a>См. также
- [Функции AlwaysOn VPN и возможности](vpn-map-da.md): В этом разделе вы узнаете о возможностях и функциях AlwaysOn VPN. 

- [Настройка VPN-туннели устройства в Windows 10](vpn-device-tunnel-config.md): AlwaysOn VPN дает возможность создать профиль VPN, выделенный для устройства или компьютера. Всегда на VPN-подключения включают два типа туннелей: _туннель устройства_ и _туннель пользователя_. Туннель устройства используется для сценариев предварительного подключения и управления устройства. Туннель пользователя позволяет пользователям получить доступ к ресурсам организации через VPN-серверов.

- [Always On развертывание VPN для Windows Server 2016 и Windows 10](always-on-vpn/deploy/always-on-vpn-deploy.md): Инструкции по развертыванию удаленного доступа как один клиент удаленного доступа VPN-шлюза для подключений VPN между сайтами, которые позволяют сотрудникам удаленного подключения к сети организации, всегда на VPN-подключения. Рекомендуется ознакомиться с руководства по разработке и развертыванию для каждой из технологий, которые используются в этом развертывании.

- [Техническое руководство по VPN Windows 10](https://docs.microsoft.com/windows/access-protection/vpn/vpn-guide): Руководство по решения необходимо будет сделать для клиентов Windows 10 в вашей организации решение VPN и способы настройки развертывания. Можно найти ссылки на поставщика службы конфигурации VPNv2 (CSP) и обеспечивает управление мобильными устройствами (MDM) инструкции по настройке с помощью Microsoft Intune и шаблоном профиля VPN для Windows 10.

- [Создание профилей VPN в System Center Configuration Manager как](https://docs.microsoft.com/sccm/protect/deploy-use/create-vpn-profiles): В этом разделе вы узнаете, как создать профили VPN в System Center Configuration Manager (SCCM).

- [Настройка клиента Windows 10 AlwaysOn VPN-подключений](https://docs.microsoft.com/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/vpn-deploy-client-vpn-connections): В этом разделе описывается ProfileXML параметры и схему и как создать VPN-Подключение ProfileXML. После установки инфраструктуры сервера, необходимо настроить клиентские компьютеры Windows 10 для взаимодействия с этой инфраструктурой с помощью VPN-подключения.

- [Параметры для профиля VPN](https://docs.microsoft.com/windows/access-protection/vpn/vpn-profile-options): В этом разделе описываются параметры профиля VPN в Windows 10 и сведения о настройке профилей VPN с помощью Intune или SCCM. Можно настроить все параметры VPN в Windows 10 с помощью узла ProfileXML в VPNv2 CSP.
