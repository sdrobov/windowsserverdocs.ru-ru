---
title: Локальные компоненты клиента
description: Описывает локальные компоненты в развертывании служб удаленных рабочих столов.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: remote-desktop-services
ms.author: elizapo
ms.date: 08/01/2016
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b3eebb38-a835-4fa6-9e41-1966014bf2cb
author: lizap
manager: dongill
ms.openlocfilehash: 191d2247af5d5f63a203415af13f8d3370b3c6f6
ms.sourcegitcommit: 0467b8e69de66e3184a42440dd55cccca584ba95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69546478"
---
# <a name="tenant-on-premises-components"></a>Локальные компоненты клиента

>Относится к: Windows Server (Semi-Annual Channel), Windows Server 2019, Windows Server 2016

Следующие сведения описывают локальные компоненты, составляющие развертывание по размещению рабочих столов.  
  
##  <a name="clients"></a>Клиенты  
Чтобы получить доступ к размещенным рабочим столам и приложениям, пользователи должны использовать клиенты удаленного рабочего стола, которые поддерживают протокол удаленного рабочего стола (RDP) 7.1 или более поздней версии. В частности, клиент должен поддерживать шлюз удаленных рабочих столов и посредник подключений к удаленному рабочему столу. Для предоставления приложений на локальном рабочем столе клиент должен также поддерживать функцию RemoteApp. Чтобы добиться максимальной масштабируемости шлюза, клиент должен поддерживать чистый транспорт HTTP для подключений к шлюзу удаленных рабочих столов.  
  
Дополнительные сведения:  
[Устройства с поддержкой RemoteFX](https://social.technet.microsoft.com/wiki/contents/articles/14534.remotefx-enabled-devices.aspx)  
[Новые возможности шлюза удаленных рабочих столов в Windows Server 2012 R2](https://blogs.technet.microsoft.com/enterprisemobility/2013/03/14/whats-new-in-windows-server-2012-remote-desktop-gateway/#transport)  
[Клиенты удаленного рабочего стола (Майкрософт)](https://technet.microsoft.com/library/dn473009.aspx)  
[Приложение удаленного рабочего стола для Windows в Microsoft Store](https://apps.microsoft.com/windows/app/remote-desktop/051f560e-5e9b-4dad-8b2e-fa5e0b05a480)  
[Удаленный рабочий стол — приложения для Android в Google Play](https://play.google.com/store/apps/details?id=com.microsoft.rdc.android)  
[Mac App Store — удаленный рабочий стол (Майкрософт)](https://itunes.apple.com/app/microsoft-remote-desktop/id715768417?mt=12)  
[Удаленный рабочий стол (Майкрософт) в App Store](https://itunes.apple.com/app/microsoft-remote-desktop/id714464092?mt=8)  
  
##  <a name="active-directory-domain-services"></a>Доменные службы Active Directory  
Некоторые большие и более сложные клиенты могут разместить сервер доменных служб Active Directory (AD DS) в своей локальной среде. В этом случае сервер AD DS в среде клиента, как правило, будет репликой сервера AD DS, который находится в локальной среде клиента. Это поддерживается путем создания виртуальной сети в среде клиента и использования VPN-шлюза Azure для создания подключения "сеть — сеть" из локальной сети клиента к виртуальной сети клиента в центре обработки данных Azure.  
  
Дополнительные сведения:  
[Обзор виртуальной сети Microsoft Azure](https://azure.microsoft.com/documentation/articles/virtual-networks-overview/)  
[Создание виртуальной сети диспетчера ресурсов с VPN-подключением типа "сеть — сеть" с помощью портала Azure](https://azure.microsoft.com/documentation/articles/vpn-gateway-howto-site-to-site-resource-manager-portal/)  


