---
title: Виртуальная частная сеть (VPN)
description: С помощью этого раздела вы узнаете о возможностях и функциях VPN в Windows Server 2016 и Windows 10.
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: cd4908f0-0d6f-4c02-8f98-4dc88c3dcb65
ms.date: 11/05/2018
ms.author: pashort
author: shortpatti
ms.localizationpriority: medium
ms.openlocfilehash: 6b647d8cbf9586408b49c1519b57d32e596fce10
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71404223"
---
# <a name="virtual-private-networking-vpn"></a>Виртуальная частная сеть (VPN)

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows 10

## <a name="ras-gateway-as-a-single-tenant-vpn-server"></a>Шлюз RAS в качестве VPN-сервера одного клиента

В Windows Server 2016 роль сервера удаленного доступа является логическим группированием следующих связанных технологий доступа к сети.

- Служба удаленного доступа (RAS)
- Маршрутизация
- Прокси-сервер веб-приложения

Эти технологии являются службами роли сервера удаленного доступа.

При установке роли сервера удаленного доступа с помощью мастера добавления ролей и компонентов или Windows PowerShell можно установить одну или несколько из этих трех служб ролей.

При установке службы роли **DirectAccess и VPN** развертывается шлюз службы удаленного доступа (**шлюз RAS**). Шлюз RAS можно развернуть как отдельный сервер виртуальной частной сети (VPN) шлюза RAS, который предоставляет множество дополнительных функций и улучшенные функциональные возможности.

>[!NOTE]
>Вы также можете развернуть шлюз RAS в качестве VPN-сервера с многопользовательским интерфейсом для использования с программно заданной сетью (SDN) или как сервер DirectAccess. Дополнительные сведения см. в статье [шлюз RAS](https://docs.microsoft.com/windows-server/remote/remote-access/ras-gateway/ras-gateway), [программно-определяемая сеть (SDN)](https://docs.microsoft.com/windows-server/networking/sdn/software-defined-networking)и [DirectAccess](https://docs.microsoft.com/windows-server/remote/remote-access/directaccess/directaccess).

## <a name="related-topics"></a>См. также
- [Always on функции и функции VPN](vpn-map-da.md): В этом разделе вы узнаете о функциях и функциях Always On VPN. 

- [Настройка туннелей VPN-устройств в Windows 10](vpn-device-tunnel-config.md): Always On VPN предоставляет возможность создания выделенного профиля VPN для устройства или компьютера. Always On VPN-подключения включают два типа туннелей: _туннель устройства_ и _туннель пользователя_. Туннель устройства используется для сценариев подключения предварительного входа и управления устройствами. Пользовательский туннель позволяет пользователям получать доступ к ресурсам Организации через VPN-серверы.

- [Always on развертывание VPN для Windows Server 2016 и Windows 10](always-on-vpn/deploy/always-on-vpn-deploy.md): Содержит инструкции по развертыванию удаленного доступа в качестве отдельного VPN-шлюза RAS для VPN-подключений типа "точка — сеть", которые позволяют удаленным сотрудникам подключаться к сети Организации с Always On VPN-подключениями. Рекомендуется ознакомиться с руководством по проектированию и развертыванию для каждой из технологий, используемых в этом развертывании.

- [Техническое руководство по VPN Windows 10](https://docs.microsoft.com/windows/access-protection/vpn/vpn-guide): Пошаговые инструкции по решениям для клиентов Windows 10 в корпоративном VPN-решении и настройке развертывания. Можно найти ссылки на поставщика службы настройки поддержка vpnv2 (CSP) и предоставить инструкции по настройке управления мобильными устройствами (MDM) с помощью Microsoft Intune и шаблона профиля VPN для Windows 10.

- [Создание профилей VPN в System Center Configuration Manager](https://docs.microsoft.com/sccm/protect/deploy-use/create-vpn-profiles): В этом разделе вы узнаете, как создавать профили VPN в System Center Configuration Manager (SCCM).

- [Настройка клиента Windows 10 Always on VPN-подключений](https://docs.microsoft.com/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/vpn-deploy-client-vpn-connections): В этом разделе описываются параметры и схема Профилексмл, а также описывается создание Профилексмл VPN. После настройки серверной инфраструктуры необходимо настроить клиентские компьютеры Windows 10 для связи с этой инфраструктурой с помощью VPN-подключения.

- [Параметры профиля VPN](https://docs.microsoft.com/windows/access-protection/vpn/vpn-profile-options): В этом разделе описываются параметры профиля VPN в Windows 10 и настраиваются профили VPN с помощью Intune или SCCM. Вы можете настроить все параметры VPN в Windows 10 с помощью узла Профилексмл в поставщике служб шифрования поддержка vpnv2.
