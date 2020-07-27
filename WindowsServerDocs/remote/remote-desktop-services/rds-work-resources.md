---
title: Настройка заголовка "Рабочие ресурсы" для RDS с помощью PowerShell в Windows Server
description: Содержит описание того, как можно изменить имя рабочей области по умолчанию в Windows Server.
ms.prod: windows-server
ms.technology: remote-desktop-services
ms.author: helohr
ms.date: 10/26/2017
ms.topic: article
author: Heidilohr
ms.openlocfilehash: ec07fe6c93f1f2c3350af7a9bd0bc2be0a384b93
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86963246"
---
# <a name="customize-the-rds-title-work-resources-using-powershell-on-windows-server"></a>Настройка заголовка "Рабочие ресурсы" для RDS с помощью PowerShell в Windows Server

При использовании Windows Server для доступа к удаленным приложениям RemoteApp или рабочим столам посредством веб-доступа к удаленному рабочему столу или нового приложения "Удаленный рабочий стол" вы могли заметить, что рабочая область по умолчанию называется "Рабочие ресурсы".  Можно легко изменить этот заголовок с помощью командлетов PowerShell.

Для этого откройте новое окно PowerShell на сервере посредника подключений и импортируйте модуль RemoteDesktop с помощью следующей команды.

```powershell
    Import-Module RemoteDesktop
```

Затем используйте команду Set-RDWorkspace для изменения имени рабочей области.

```powershell
    Set-RDWorkspace [-Name] <string> [-ConnectionBroker <string>]  [<CommonParameters>]
```   

Например, можно использовать следующую команду для изменения имени рабочей области на "Contoso RemoteApps".

```powershell
    Set-RDWorkspace -Name "Contoso RemoteApps" -ConnectionBroker broker01.contoso.com
```

Если вы используете несколько посредников подключений в режиме высокой доступности, эту команду необходимо выполнить для активного посредника. Можно использовать приведенную ниже команду.

```powershell
    Set-RDWorkspace -Name "Contoso RemoteApps" -ConnectionBroker (Get-RDConnectionBrokerHighAvailability).ActiveManagementServer
```

Дополнительные сведения о командлете Set-RDWorkspace см. в справочных материалах по [Set-RDWorkspace](/powershell/module/remotedesktop/set-rdworkspace?view=win10-ps).
