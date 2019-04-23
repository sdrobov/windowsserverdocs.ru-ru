---
title: Настройка заголовка "Рабочие ресурсы" для RDS с помощью PowerShell на Windows Server
description: Содержит описание того, как можно изменить имя рабочей области по умолчанию в Windows Server.
ms.prod: windows-server-threshold
ms.technology: remote-desktop-services
ms.author: helohr
ms.date: 10/26/2017
ms.topic: article
author: Heidilohr
ms.openlocfilehash: 43837826a6cddc2c3c4c7c1af874334718a3a067
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59826715"
---
# <a name="customize-the-rds-title-work-resources-using-powershell-on-windows-server"></a>Настройка заголовка "Рабочие ресурсы" для RDS с помощью PowerShell на Windows Server

При использовании Windows Server для доступа к приложения RemoteApp или рабочие столы через веб-клиент к удаленному рабочему Столу или новое приложение удаленного рабочего стола, вы могли заметить, рабочей области называется «Рабочие материалы» по умолчанию.  Можно легко изменить заголовок с помощью командлетов PowerShell.

Изменение заголовка, откройте новое окно PowerShell на сервере посредника подключений и импортируйте модуль удаленный рабочий стол с помощью следующей команды.

```powershell
    Import-Module RemoteDesktop
```

Затем используйте команду Set-RDWorkspace для изменения имени рабочей области.

```powershell
    Set-RDWorkspace [-Name] <string> [-ConnectionBroker <string>]  [<CommonParameters>]
```   

Например можно использовать следующую команду для изменения имени рабочей на «Contoso RemoteApps»:

```powershell
    Set-RDWorkspace -Name "Contoso RemoteApps" -ConnectionBroker broker01.contoso.com
```

Если вы используете несколько посредников подключений в режиме высокой доступности, эту команду необходимо выполнить для активный broker. Можно использовать эту команду:

```powershell
    Set-RDWorkspace -Name "Contoso RemoteApps" -ConnectionBroker (Get-RDConnectionBrokerHighAvailability).ActiveManagementServer
```

Дополнительные сведения о командлете Set-RDWorkspace см. в разделе [RDSWorkspace набора](https://docs.microsoft.com/powershell/module/remotedesktop/set-rdworkspace?view=win10-ps) ссылки.