---
title: Get — Namespace
description: Раздел команд Windows для Get-Namespace, в котором отображаются сведения о пользовательском пространстве имен.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ea641bab-e97b-4909-918e-447730027dc1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 58e84ec5c82ea3c2663b38bd2e53f65f2cf47519
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80830887"
---
# <a name="get-namespace"></a>Get — Namespace

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает сведения о пользовательском пространстве имен.

## <a name="syntax"></a>Синтаксис
Windows Server 2008 R2
```
wdsutil /Get-Namespace /Namespace:<Namespace name> [/Server:<Server name>] [/Show:Clients]
```
Windows Server 2008 R2
```
wdsutil /Get-Namespace /Namespace:<Namespace name> [/Server:<Server name>] [/details:Clients]
```
### <a name="parameters"></a>Параметры

|               Параметр               |                                                                                                                                                                                         Описание                                                                                                                                                                                          |
|---------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      /Namespace:<Namespace name>      | Указывает имя пространства имен. Обратите внимание, что это не понятное имя, оно должно быть уникальным.<p>-Сервер развертывания. синтаксис имени пространства имен —/Намспаце: WDS:<ImageGroup>/<ImageName>/<Index>. Например: **WDS: ImageGroup1/install. wim/1**<br />— Транспортный сервер. это значение должно совпадать с именем, присвоенным пространству имен при его создании на сервере. |
|        [/Server:<Server name>]        |                                                                                                             Указывает имя сервера. Это может быть NetBIOS-имя или полное доменное имя (FQDN). Если имя сервера не указано, используется локальный сервер.                                                                                                              |
| [/Show: Clients] или [/детаилс: Clients] |                                                                                                                                                  Отображает сведения о клиентских компьютерах, подключенных к указанному пространству имен.                                                                                                                                                  |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы просмотреть сведения о пространстве имен, введите:
```
wdsutil /Get-Namespace /Namespace:Custom Auto 1
```
Чтобы просмотреть сведения о пространстве имен и подключенных клиентах, введите одно из следующих действий:
- Windows Server 2008: `wdsutil /Get-Namespace /Server:MyWDSServer /Namespace:Custom Auto 1 /Show:Clients`
- Windows Server 2008 R2: `wdsutil /Get-Namespace /Server:MyWDSServer /Namespace:Custom Auto 1 /details:Clients`
  ## <a name="additional-references"></a>Дополнительные материалы
  - [Ключ синтаксиса командной строки](command-line-syntax-key.md)
  [с помощью команды Get-Аллнамеспацес,](using-the-get-allnamespaces-command.md)
  [помощью команды New-Namespace](using-the-new-namespace-command.md)
  [помощью команды Remove-Namespace,](using-the-remove-namespace-command.md)
  [подкоманде: Start-Namespace.](subcommand-start-namespace.md)
