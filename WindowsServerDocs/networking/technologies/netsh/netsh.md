---
title: Сетевой оболочки (Netsh)
description: В этом разделе представлен обзор служебной программы командной строки Network Shell (netsh) в Windows Server 2016.
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: aedef092-8445-4e53-b9d4-525ecd98b02d
manager: brianlic
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 0a23d60bc3f181fee62ade105e546bbb7161c133
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="network-shell-netsh"></a>Сетевая оболочка \(Netsh\)

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

Сетевой оболочки (netsh) — средство командной строки, которая позволяет настраивать и отображать состояние различных сетевых ролей коммуникационных серверов и компонентов после их установки на компьютерах под управлением Windows Server 2016.

>[!NOTE]
>Дополнение к данному разделу доступна следующее содержимое сетевой оболочки.
>
> - [Синтаксис команд Netsh, контексты и форматирование](netsh-contexts.md)
> - [Сетевой оболочки (Netsh) пример пакетного файла](netsh-wins.md)
> - [Netsh Технический справочник](https://gallery.technet.microsoft.com/Netsh-Technical-Reference-c46523dc) 

Некоторые технологии клиента, такие как \(DHCP\) Dynamic Host Configuration Protocol клиента и BranchCache, также предоставляют команды netsh для настройки клиентских компьютеров, работающих под управлением Windows 10.

В большинстве случаев команды netsh предоставляют те же функциональные возможности, которая доступна при использовании консоли управления \(MMC\) snap\-в для каждого сетевого компонента роли или сети сервера. Например, можно настроить \(NPS\) сервера политики сети с помощью оснастки NPS MMC или команды netsh в **netsh nps** контекста.

Кроме того существует команды netsh для сетевой технологии, такие как IPv6, сетевой мост и \(RPC\) удаленного вызова процедур, которые недоступны в Windows Server как оснастки MMC.

>[!IMPORTANT]
>Рекомендуется использовать Windows PowerShell для управления сетевых возможностей в [Windows Server 2016 и Windows 10](https://technet.microsoft.com/library/mt156917.aspx) вместо сетевой оболочки. Сетевой оболочки включен для обеспечения совместимости с сценарии, тем не менее, и его использование поддерживается.

## <a name="network-shell-netsh-technical-reference"></a>Технический справочник сетевой оболочки (Netsh)

Технический справочник по Netsh предоставляет полной справочник команд netsh, включая синтаксис, параметры и примеры для команды netsh. Технический справочник по Netsh можно использовать для создания сценариев и пакетных файлов с помощью команды netsh для локального или удаленного управления технологиями сети на компьютерах под управлением Windows Server 2016 и Windows 10.  
  
### <a name="content-availability"></a>Доступности содержимого  
  
Сети Технический справочник по командной доступен для загрузки в формате \(*.chm\) справки Windows из галереи TechNet: [Технический справочник по Netsh](https://gallery.technet.microsoft.com/Netsh-Technical-Reference-c46523dc)  
  

