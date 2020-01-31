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
ms.openlocfilehash: fdd409dee5a7a957580daeeb05209336edfd86f6
ms.sourcegitcommit: 07c9d4ea72528401314e2789e3bc2e688fc96001
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/29/2020
ms.locfileid: "76822617"
---
# <a name="virtual-private-networking-vpn"></a>Виртуальная частная сеть (VPN)

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows 10

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

## <a name="related-topics"></a>Связанные темы
- [Always on функции и функции VPN](vpn-map-da.md). в этом разделе вы узнаете о функциях и функциях Always on VPN. 

- [Настройка туннелей VPN-устройств в Windows 10](vpn-device-tunnel-config.md): Always on VPN предоставляет возможность создания выделенного профиля VPN для устройства или компьютера. Always On VPN-подключения включают два типа туннелей: _туннель устройства_ и _туннель пользователя_. Туннель устройства используется для сценариев подключения предварительного входа и управления устройствами. Пользовательский туннель позволяет пользователям получать доступ к ресурсам Организации через VPN-серверы.

- [Always on развертывание VPN для Windows Server 2016 и Windows 10](always-on-vpn/deploy/always-on-vpn-deploy.md): содержит инструкции по развертыванию удаленного доступа в качестве одного VPN-шлюза RAS для VPN-подключений типа "точка — сеть", которые позволяют удаленным сотрудникам подключаться к сети организации с Always on VPN-подключениями. Рекомендуется ознакомиться с руководством по проектированию и развертыванию для каждой из технологий, используемых в этом развертывании.

- [Техническое руководство по VPN Windows 10](https://docs.microsoft.com/windows/access-protection/vpn/vpn-guide). пошаговые инструкции по принятию решений для клиентов Windows 10 в корпоративном VPN-решении и настройке развертывания. Можно найти ссылки на поставщика службы настройки поддержка vpnv2 (CSP) и предоставить инструкции по настройке управления мобильными устройствами (MDM) с помощью Microsoft Intune и шаблона профиля VPN для Windows 10.

- [Создание профилей VPN в Configuration Manager](https://docs.microsoft.com/configmgr/protect/deploy-use/create-vpn-profiles). в этом разделе вы узнаете, как создавать профили vpn в Configuration Manager.

- [Настройка клиента Windows 10 Always on VPN-подключениях](https://docs.microsoft.com/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/vpn-deploy-client-vpn-connections). в этом разделе описываются параметры и схема профилексмл, а также создание VPN профилексмл. После настройки серверной инфраструктуры необходимо настроить клиентские компьютеры Windows 10 для связи с этой инфраструктурой с помощью VPN-подключения.

- [Параметры профиля VPN](https://docs.microsoft.com/windows/access-protection/vpn/vpn-profile-options). в этом разделе описываются параметры профиля VPN в Windows 10 и настраиваются профили VPN с помощью Intune или Configuration Manager. Вы можете настроить все параметры VPN в Windows 10 с помощью узла Профилексмл в поставщике служб шифрования поддержка vpnv2.
