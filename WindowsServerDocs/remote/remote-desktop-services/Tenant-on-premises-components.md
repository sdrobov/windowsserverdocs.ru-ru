---
title: Локальные компоненты клиента
description: Описывает локальные компоненты в развертывании служб удаленных рабочих СТОЛОВ.
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
ms.openlocfilehash: a01dbd12d76b1efa84e38f2ded38cfd613fb2ac4
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59857405"
---
# <a name="tenant-on-premises-components"></a>Локальные компоненты клиента

>Область применения. Windows Server (полугодовой канал), Windows Server 2016

Следующие данные описывают локальные компоненты, составляющие развертывание по размещению рабочих столов.  
  
##  <a name="clients"></a>Клиенты  
Чтобы получить доступ к размещенной настольных систем и приложений, пользователи должны использовать клиенты удаленного рабочего стола, которые поддерживают удаленного рабочего стола (RDP) 7.1 или более поздней версии. В частности клиент должен поддерживать шлюза удаленных рабочих столов и посредника подключений к удаленному рабочему столу. Для предоставления приложений на локальный рабочий стол, клиент должен также поддерживать функцию RemoteApp. Чтобы добиться шлюза при масштабировании, клиент должен поддерживать чисто транспорта HTTP-подключений к шлюзу удаленных рабочих Столов.  
  
Дополнительные сведения:  
[Устройства с поддержкой RemoteFX](https://social.technet.microsoft.com/wiki/contents/articles/14534.remotefx-enabled-devices.aspx)  
[Новые возможности в Windows Server 2012 R2 шлюза удаленных рабочих столов](https://blogs.technet.microsoft.com/enterprisemobility/2013/03/14/whats-new-in-windows-server-2012-remote-desktop-gateway/#transport)  
[Клиенты Microsoft удаленного рабочего стола](https://technet.microsoft.com/library/dn473009.aspx)  
[Приложение удаленного рабочего стола для Windows в Microsoft Store](https://apps.microsoft.com/windows/app/remote-desktop/051f560e-5e9b-4dad-8b2e-fa5e0b05a480)  
[Microsoft Remote Desktop — приложений Android в Google Play](https://play.google.com/store/apps/details?id=com.microsoft.rdc.android)  
[Mac App Store - удаленного рабочего стола](https://itunes.apple.com/us/app/microsoft-remote-desktop/id715768417?mt=12)  
[Удаленного рабочего стола в App Store](https://itunes.apple.com/us/app/microsoft-remote-desktop/id714464092?mt=8)  
  
##  <a name="active-directory-domain-services"></a>Доменные службы Active Directory  
Некоторые клиенты большего размера и более сложные можете разместить сервер доменных служб Active Directory (AD DS) в своей локальной среде. В этом случае сервера AD DS в среде клиента как правило, будет реплика сервера AD DS, который находится в локальной среде клиента. Это поддерживается путем создания виртуальной сети в среде клиента и с помощью VPN-ШЛЮЗА Azure для создания подключения сеть сеть из локальной сети клиента к виртуальной сети клиента в центре обработки данных Azure.  
  
Дополнительные сведения:  
[Обзор виртуальной сети Microsoft Azure](https://azure.microsoft.com/documentation/articles/virtual-networks-overview/)  
[Создать ресурс диспетчера виртуальной сети с подключением типа сеть-сеть VPN, с помощью портала Azure](https://azure.microsoft.com/documentation/articles/vpn-gateway-howto-site-to-site-resource-manager-portal/)  


