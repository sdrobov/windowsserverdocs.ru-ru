---
title: Сетевая оболочка (Netsh)
description: Здесь представлен обзор служебной программы командной строки Network Shell (netsh) в Windows Server 2016.
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: aedef092-8445-4e53-b9d4-525ecd98b02d
manager: dougkim
ms.author: pashort
author: shortpatti
ms.date: 09/13/2018
ms.openlocfilehash: 038b21783ef1d27619657ec3f9a472cf3caba68e
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59849365"
---
# <a name="network-shell-netsh"></a>Сетевой оболочки \(Netsh\)

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

Сетевой оболочки (netsh) — программа командной строки, которая позволяет настраивать и отображать состояние различных сетевых ролей коммуникационных серверов и компонентов после их установки на компьютерах под управлением Windows Server 2016.

Некоторые клиентские технологии, такие как Dynamic Host Configuration Protocol \(DHCP\) клиента и BranchCache, также предоставляют команд netsh, которые дают возможность настраивать клиентских компьютеров, работающих под управлением Windows 10.

В большинстве случаев команды netsh обеспечивают ту же функциональность, которая доступна при использовании консоли управления \(MMC\) привязать\-в для каждого сетевого компонента роли или журнал сетевых подключений сервера. Например, можно настроить сервер политики сети \(NPS\) с помощью оснастки NPS MMC или команды netsh в **netsh nps** контекста.

Кроме того, есть команды netsh для сетевой технологии, такие как IPv6, сетевой мост и удаленный вызов процедуры \(RPC\), недоступные в Windows Server как оснастки MMC.

>[!IMPORTANT]
>Рекомендуется использовать Windows PowerShell для управления сетевые технологии в [Windows Server 2016 и Windows 10](https://technet.microsoft.com/library/mt156917.aspx) вместо того чтобы сетевой оболочки. Network Shell включено для совместимости со сценариями, тем не менее, и его использование поддерживается.

## <a name="network-shell-netsh-technical-reference"></a>Технический справочник по сети оболочки (Netsh)

Технический справочник по Netsh предоставляет полный Справочник по командам, включая синтаксис, параметры и примеры для команды netsh. Технический справочник по Netsh можно использовать для создания сценариев и пакетных файлов с помощью команды netsh для управления локальным или удаленным сетевых технологий на компьютерах под управлением Windows Server 2016 и Windows 10.  
  
### <a name="content-availability"></a>Доступность содержимого  
  
Технический справочник по командной сети доступно для загрузки в справке Windows \(*.chm\) формате из коллекции TechNet: [Netsh Технический справочник](https://gallery.technet.microsoft.com/Netsh-Technical-Reference-c46523dc)  
  
---
