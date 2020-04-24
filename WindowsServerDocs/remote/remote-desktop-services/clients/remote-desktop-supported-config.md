---
title: Клиент удаленного рабочего стола — поддерживаемые конфигурации
description: Узнайте, какие компьютеры доступны с помощью клиентов удаленного рабочего стола
ms.prod: windows-server
ms.technology: remote-desktop-services
ms.topic: article
ms.assetid: bb932dad-6f74-484f-8f7b-dd957b615d44
author: lizap
manager: dongill
ms.author: elizapo
ms.date: 06/05/2018
ms.localizationpriority: medium
ms.openlocfilehash: 1480a2a14a1c3fc23c4e5122e366741d37d9091f
ms.sourcegitcommit: 3a3d62f938322849f81ee9ec01186b3e7ab90fe0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2020
ms.locfileid: "80856017"
---
# <a name="remote-desktop-client---supported-configuration"></a>Клиент удаленного рабочего стола — поддерживаемые конфигурации

## <a name="supported-pcs"></a>Поддерживаемые ПК
Вы можете подключаться к ПК, работающим под управлением следующих операционных систем Windows:
- Windows 10 Pro
- Windows 10 Корпоративная
- Windows 8 Корпоративная
- Windows 8 Профессиональная
- Windows 7 Профессиональная
- Windows 7 Корпоративная
- Windows 7 Максимальная
- Windows 7 Максимальная
- Windows Server 2008
- Windows Server 2008 R2
- Windows Server 2012
- Windows Server 2012 R2
- Windows Server 2016
- Windows Multipoint Server 2011
- Windows Multipoint Server 2012
- Windows Small Business Server 2008
- Windows Small Business Server 2011

Следующие компьютеры позволяют запускать шлюз удаленных рабочих столов:

- Windows Server 2008
- Windows Server 2008 R2
- Windows Server 2012
- Windows Server 2012 R2
- Windows Server 2016
- Windows Small Business Server 2011

Следующие операционные системы можно использовать в качестве серверов веб-доступа к удаленным рабочим столам и приложениям RemoteApp:
- Windows Server 2008 R2
- Windows Server 2012
- Windows Server 2012 R2
- Windows Server 2016

## <a name="unsupported-windows-versions-and-editions"></a>Неподдерживаемые версии и выпуски Windows

Клиент удаленного рабочего стола не может подключаться к этим версиям и выпускам Windows:

- Windows 7 Начальная
- Windows 7 Домашняя
- Windows 8 Домашняя
- Windows 8.1 Домашняя
- Windows 10 Домашняя

Если требуется получать доступ к компьютерам, где работает одна из этих версий Windows, рекомендуется обновить его до версии Windows, которая поддерживает протокол удаленного рабочего стола.

## <a name="rd-gateway-messaging-is-not-supported"></a>Обмен сообщениями шлюза удаленных рабочих столов не поддерживается
Клиент удаленного рабочего стола не поддерживает обмен сообщениями шлюза удаленных рабочих столов. Убедитесь, что политика удаленного доступа удаленного рабочего стола (RD RAP) для вашего сервера шлюза удаленных рабочих столов не задает параметр **Разрешить только компьютеры с поддержкой обмена сообщениями шлюза удаленных рабочих столов**, иначе вы не сможете подключиться.