---
title: Сетевая оболочка (Netsh)
description: В этом разделе содержится обзор служебной программы командной строки Network Shell (Netsh) в Windows Server 2016.
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: aedef092-8445-4e53-b9d4-525ecd98b02d
manager: dougkim
ms.author: pashort
author: shortpatti
ms.date: 09/13/2018
ms.openlocfilehash: ac440c8187424733c0636cf2013342458f08d2f4
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71405548"
---
# <a name="network-shell-netsh"></a>Сетевая оболочка \(Netsh\)

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

Сетевая оболочка (Netsh) — это программа командной строки, которая позволяет настраивать и отображать состояние различных ролей и компонентов сервера сетевого взаимодействия после их установки на компьютерах под управлением Windows Server 2016.

Некоторые клиентские технологии, такие как протокол динамической настройки узла \(DHCP-\) Client и BranchCache, также предоставляют команды Netsh, позволяющие настраивать клиентские компьютеры под управлением Windows 10.

В большинстве случаев команды netsh предоставляют те же функциональные возможности, которые доступны при использовании консоли управления (Майкрософт) \(MMC\) привязать\-в для каждой роли сетевого сервера или сетевого компонента. Например, можно настроить сервер политики сети \(\) NPS с помощью оснастки консоли управления (NPS) или команд Netsh в контексте **netsh nps** .

Кроме того, существуют команды Netsh для сетевых технологий, например для IPv6, сетевого моста и удаленного вызова процедур, \(\)RPC, недоступные в Windows Server в качестве оснастки MMC.

>[!IMPORTANT]
>Для управления сетевыми технологиями в [Windows Server 2016 и Windows 10](https://technet.microsoft.com/library/mt156917.aspx) рекомендуется использовать Windows PowerShell, а не Сетевая оболочка. Сетевая оболочка включена для обеспечения совместимости с вашими скриптами, но поддерживается ее использование.

## <a name="network-shell-netsh-technical-reference"></a>Технический справочник по сетевой оболочке (Netsh)

Технический справочник по Netsh содержит исчерпывающую справочную информацию по командам Netsh, включая синтаксис, параметры и примеры команд Netsh. Технический справочник по Netsh можно использовать для создания сценариев и пакетных файлов с помощью команд Netsh для локального или удаленного управления сетевыми технологиями на компьютерах под управлением Windows Server 2016 и Windows 10.  
  
### <a name="content-availability"></a>Доступность содержимого  
  
Технический справочник по сетевой оболочке доступен для загрузки в справке Windows \(*. chm\) формате из коллекции TechNet: [netsh Technical Reference](https://gallery.technet.microsoft.com/Netsh-Technical-Reference-c46523dc)  
  
---
