---
title: Клиент удаленного рабочего стола - поддерживаемые конфигурации
description: Узнайте, какие ПК, доступных с помощью клиентов удаленного рабочего стола
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
ms.sourcegitcommit: 96e968bbe8dc50ebb1535ae1c8ce92fa73c83171
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "1978051"
---
# <a name="remote-desktop-client---supported-configuration"></a>Клиент удаленного рабочего стола - поддерживаемые конфигурации

## <a name="supported-pcs"></a>Поддерживаемые ПК
Возможность подключения к ПК, работающих под управлением следующих операционных систем Windows:
- Windows10 Pro
- Windows10 Корпоративная
- Windows 8 Корпоративная
- Windows 8 Профессиональная
- Windows 7 Профессиональная
- Windows 7 Корпоративная
- Windows 7 Максимальная
- Windows 7 Максимальная
- Windows Server 2008
- Windows Server 2008 R2
- Windows Server 2012
- Windows Server 2012 R2
- WindowsServer2016
- Windows Server многоточечных 2011 г.
- Многоточечных Windows Server 2012 г.
- Windows Small Business Server 2008
- Windows Small Business Server 2011

Следующие компьютеры можно запустить на шлюз удаленных рабочих столов:

- Windows Server 2008
- Windows Server 2008 R2
- Windows Server 2012
- Windows Server 2012 R2
- WindowsServer2016
- Windows Small Business Server 2011

В следующих операционных системах может выступать в качестве веб-клиента удаленных рабочих Столов или удаленных приложений RemoteApp серверов:
- Windows Server 2008 R2
- Windows Server 2012
- Windows Server 2012 R2
- WindowsServer2016

## <a name="unsupported-windows-versions-and-editions"></a>Неподдерживаемые Windows версии и выпуска

Клиент удаленного рабочего стола не будет подключиться к эти выпуски и версии Windows:

- Windows 7 Начальная
- Домашняя страница Windows 7
- Домашняя страница Windows 8
- Домашняя страница Windows 8.1
- Windows 10 Домашняя

Если вы хотите получить доступ к компьютерам с одним из следующих версий Windows, рекомендуется обновление до версии Windows, которая поддерживает RDP.

## <a name="rd-gateway-messaging-is-not-supported"></a>Система обмена сообщениями шлюза удаленных рабочих Столов не поддерживается
Клиент удаленного рабочего стола не поддерживает шлюза удаленных рабочих Столов системы обмена сообщениями. Убедитесь, что рабочий стол ресурсов политики удаленного доступа (ПОЛИТИКИ) для шлюза удаленных рабочих Столов не определяет, **разрешены только компьютеры с поддержкой системы обмена сообщениями шлюз удаленных рабочих Столов** , или вы не сможете подключиться.