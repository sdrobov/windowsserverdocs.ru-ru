---
title: Виртуальная частная сеть (VPN)
description: Дополнительные сведения о Windows Server 2016 и VPN в Windows 10 функции и возможности можно использовать в этом разделе.
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: cd4908f0-0d6f-4c02-8f98-4dc88c3dcb65
ms.date: 11/05/2018
ms.author: pashort
author: shortpatti
ms.localizationpriority: medium
ms.openlocfilehash: bf38995f0a2b396044d1f45b45eff8c3c2de329d
ms.sourcegitcommit: 4893d79345cea85db427224bb106fc1bf88ffdbc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2018
ms.locfileid: "6067477"
---
# Виртуальные частные сети \(VPN\)

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows 10

## Шлюз RAS-сервера как один клиент VPN-сервера

В Windows Server 2016 роли сервера удаленного доступа — логическую группировку следующих связанных сетевых технологий доступа.

- Служба удаленного доступа (RAS)
- Маршрутизация
- Прокси-служба веб-приложения

Эти технологии — роль службы роли сервера удаленного доступа.

При установке роли сервера удаленного доступа с помощью добавления ролей и компонентов мастер или Windows PowerShell, можно установить одно или несколько из этих трех роль служб.

При установке службы роли **DirectAccess и VPN (RAS)** , вы развертываете службу шлюза удаленных доступа \ (**Шлюз RAS-сервера**\). Вы можете развернуть шлюз RAS-сервера как \(VPN\) сервер виртуальной частной сети одного клиента шлюз RAS-сервера, который содержит многие дополнительные функции и расширенные функции.

>[!NOTE]
>Шлюз RAS-сервера также можно развертывать как соответствующего VPN-сервера для использования с \(SDN\) программно-конфигурируемой сети или в качестве сервера DirectAccess. Дополнительные сведения см. в разделе [Шлюз RAS-сервера](https://docs.microsoft.com/windows-server/remote/remote-access/ras-gateway/ras-gateway), [Программно-конфигурируемой сети (SDN)](https://docs.microsoft.com/windows-server/networking/sdn/software-defined-networking)и [DirectAccess](https://docs.microsoft.com/windows-server/remote/remote-access/directaccess/directaccess).

## Смежные разделы
- [VPN функции и возможности](vpn-map-da.md): В этом разделе вы узнаете о функциях и возможностях VPN. 

- [Настройка устройства Туннели VPN в Windows 10](vpn-device-tunnel-config.md): VPN дает возможность создания специальной профиль VPN для устройства или компьютера. Подключения VPN включают два типа туннелей: _туннеля устройства_ и _пользователя туннеля_. Туннель устройства используется для сценариев с подключением входа в систему и устройство управления целей. Туннеля пользователя позволяет пользователям получать доступ к ресурсам организации через VPN-серверов.

- [Всегда на VPN развертывания для Windows Server 2016 и Windows 10](always-on-vpn/deploy/always-on-vpn-deploy.md): содержит инструкции по развертыванию удаленного доступа как единый клиент VPN-шлюза RAS-сервера для VPN-подключений точности\ to\ узла, позволяющие удаленным сотрудникам для подключения к вашей организации сеть с помощью подключения VPN. Рекомендуется изучить руководства по разработке и развертыванию для каждой из технологий, которые используются в этом развертывания.

- [Технический справочник по VPN Windows10](https://docs.microsoft.com/windows/access-protection/vpn/vpn-guide): описана решения необходимо принять для клиентов Windows 10 в свое решение VPN предприятия и способы настройки развертывания. Можно найти ссылки на поставщика службы конфигурации VPNv2 (CSP) и инструкции управления мобильными устройствами (MDM) с помощью Microsoft Intune и шаблона профиля VPN для Windows 10.

- [Как создать VPN-профили в System Center Configuration Manager](https://docs.microsoft.com/sccm/protect/deploy-use/create-vpn-profiles): В этом разделе вы узнаете, как создание профилей VPN в System Center Configuration Manager (SCCM).

- [Настройка Windows 10 клиента всегда на VPN-подключений](https://docs.microsoft.com/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/vpn-deploy-client-vpn-connections): в этом разделе описывается ProfileXML параметры и схемы и способы создания ProfileXML VPN. После настройки серверной инфраструктуры, необходимо настроить клиентские компьютеры Windows10 для связи с ИТ-инфраструктуры с VPN-подключение. 

- [Параметры профиля VPN](https://docs.microsoft.com/windows/access-protection/vpn/vpn-profile-options): в этом разделе описаны параметры профиля VPN в Windows 10 и сведения о настройке профилей VPN с помощью Intune или SCCM. Можно настроить все параметры VPN в Windows 10 с помощью узел ProfileXML в VPNv2 CSP.

---