---
title: Клиент удаленного рабочего стола - поддерживаемые конфигурации
description: Узнайте, каким компьютерам, которые доступны с помощью клиенты удаленного рабочего стола
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: remote-desktop-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bb932dad-6f74-484f-8f7b-dd957b615d44
author: lizap
manager: dongill
ms.author: elizapo
ms.date: 06/05/2018
ms.localizationpriority: medium
ms.openlocfilehash: d38008b6387385917ad21ce7e169b8ff3f4d18ba
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59884695"
---
# <a name="remote-desktop-client---supported-configuration"></a>Клиент удаленного рабочего стола - поддерживаемые конфигурации

## <a name="supported-pcs"></a>Поддерживаемые ПК
Можно подключиться к ПК, работающих под управлением следующих операционных систем Windows:
- Windows 10 Pro
- Windows 10 Корпоративная
- Windows 8 Корпоративная
- Windows 8 Профессиональная
- Windows 7 Профессиональная
- Windows 7 Корпоративная
- Windows 7 Максимальная
- Windows 7 Максимальная
- Windows Server 2008
- Windows Server 2008 R2
- Windows Server 2012
- Windows Server 2012 R2
- Windows Server 2016
- Windows Multipoint Server 2011
- Windows Multipoint Server 2012
- Windows Small Business Server 2008
- Windows Small Business Server 2011

Следующие компьютеры можно запускать шлюз удаленного рабочего стола:

- Windows Server 2008
- Windows Server 2008 R2
- Windows Server 2012
- Windows Server 2012 R2
- Windows Server 2016
- Windows Small Business Server 2011

Следующие операционные системы можно использовать в качестве серверов веб-доступа к удаленным рабочим Столам и приложениям RemoteApp:
- Windows Server 2008 R2
- Windows Server 2012
- Windows Server 2012 R2
- Windows Server 2016

## <a name="unsupported-windows-versions-and-editions"></a>Неподдерживаемый Windows версий и выпусков

Клиент удаленного рабочего стола не будет подключаться к этим Windows версий и выпусков:

- Windows 7 Начальная
- Windows 7 Домашняя
- Windows 8 Домашняя
- Windows 8.1 Домашняя
- Windows 10 Домашняя

Если требуется получать доступ к компьютерам, у которых один из этих версий Windows, мы рекомендуем обновить до версии Windows, которая поддерживает протокола удаленного рабочего СТОЛА.

## <a name="rd-gateway-messaging-is-not-supported"></a>Обмен сообщениями шлюза удаленных рабочих Столов не поддерживается
Клиент удаленного рабочего стола не поддерживает обмен сообщениями шлюза удаленных рабочих Столов. Убедитесь, что Desktop ресурсов политики удаленного доступа (RD RAP) для сервера шлюза удаленных рабочих Столов не указывает **разрешить только компьютеры с поддержкой для обмена сообщениями шлюза удаленных рабочих Столов** или вы не сможете подключиться.