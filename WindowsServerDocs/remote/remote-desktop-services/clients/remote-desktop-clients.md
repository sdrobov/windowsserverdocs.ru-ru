---
title: Клиенты удаленного рабочего стола
description: Узнайте о различных клиентах удаленного рабочего стола, доступных для всех ваших устройств.
ms.prod: windows-server
ms.technology: remote-desktop-services
ms.topic: article
ms.assetid: b7d8158c-aee1-4c60-8a46-40ce5595b8e8
author: HeidiLohr
manager: lizross
ms.author: helohr
ms.date: 01/07/2020
ms.localizationpriority: medium
ms.openlocfilehash: 711fa87fe697ae616d9bd8c696d29fabf1586055
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856047"
---
# <a name="remote-desktop-clients"></a>Клиенты удаленного рабочего стола

>Применяется к: Windows 10, Windows 8.1, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2

Вы можете использовать клиент удаленного рабочего стола (Майкрософт) для подключения к удаленному компьютеру и рабочим ресурсам практически из любой точки и с любого устройства. Вы можете подключаться к своему рабочему ПК и получать доступ ко всем своим приложениям, файлам и сетевым ресурсам, как если бы вы сидели за своим столом. Можно оставить открытыми приложения на работе, а затем увидеть те же приложения дома с помощью клиента удаленных рабочих столов.

Прежде чем начать, прочитайте статью о [поддерживаемой конфигурации](remote-desktop-supported-config.md), в которой описываются компьютеры, подходящие для подключения с помощью клиентов удаленного рабочего стола. Кроме того, ознакомьтесь с [часто задаваемыми вопросами о клиентах](remote-desktop-client-faq.md).

Доступны следующие клиентские приложения.

| Устройство          | Получить приложение                                                                                                  | Инструкции по установке                                                                |
|-----------------|-----------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
| Настольный компьютер с Windows | [Клиент Удаленного рабочего стола](windowsdesktop.md#install-the-client)                                               | [Приступая к работе с клиентом Удаленного рабочего стола](windowsdesktop.md) |
| Магазин Windows Store   | [Клиент Windows 10 в Microsoft Store](https://go.microsoft.com/fwlink/?LinkID=616709)                   | [Приступая к работе с клиентом Microsoft Store](windows.md)          |
| Android         | [Клиент Android в Google Play](https://play.google.com/store/apps/details?id=com.microsoft.rdc.android)     | [Приступая к работе с клиентом Android](remote-desktop-android.md) |
| iOS             | [Клиент iOS в магазине iTunes](https://itunes.apple.com/app/microsoft-remote-desktop/id714464092?mt=8)     | [Приступая к работе с клиентом iOS](remote-desktop-ios.md)         |
| macOS           | [Клиент macOS в магазине iTunes](https://itunes.apple.com/app/microsoft-remote-desktop/id1295203466?mt=12) | [Приступая к работе с клиентом macOS](remote-desktop-mac.md)       |

## <a name="configuring-the-remote-pc"></a>Настройка удаленного компьютера

Чтобы настроить удаленный компьютер перед осуществлением к нему удаленного доступа, [разрешите доступ к этому компьютеру](remote-desktop-allow-access.md).

## <a name="remote-desktop-client-uri-scheme"></a>Схема URI для клиента удаленного рабочего стола

Вы можете интегрировать функции клиентов удаленного рабочего стола на всех платформах с помощью схемы URI. Ознакомьтесь с [поддерживаемыми атрибутами URI](remote-desktop-uri.md), которые можно использовать с клиентами для iOS, Mac и Android.
