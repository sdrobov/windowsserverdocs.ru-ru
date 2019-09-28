---
title: Использование команды Get-Namespace
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ea641bab-e97b-4909-918e-447730027dc1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 607fb758db64cfc938a08b070b520fe2950aa482
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71363079"
---
# <a name="using-the-get-namespace-command"></a>Использование команды Get-Namespace

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

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
## <a name="parameters"></a>Параметры

|               Параметр               |                                                                                                                                                                                         Описание                                                                                                                                                                                          |
|---------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      /Namespace: <Namespace name>      | Указывает имя пространства имен. Обратите внимание, что это не понятное имя, оно должно быть уникальным.<br /><br />— Сервер развертывания: Синтаксис имени пространства имен —/Намспаце: WDS: <ImageGroup> @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4. Пример: **WDS: ImageGroup1/install. wim/1**<br />— Транспортный сервер: Это значение должно совпадать с именем, присвоенным пространству имен при его создании на сервере. |
|        [/Server: <Server name>]        |                                                                                                             Указывает имя сервера. Это может быть NetBIOS-имя или полное доменное имя (FQDN). Если имя сервера не указано, используется локальный сервер.                                                                                                              |
| [/Show: Clients] или [/детаилс: Clients] |                                                                                                                                                  Отображает сведения о клиентских компьютерах, подключенных к указанному пространству имен.                                                                                                                                                  |

## <a name="BKMK_examples"></a>Примеров
Чтобы просмотреть сведения о пространстве имен, введите:
```
wdsutil /Get-Namespace /Namespace:"Custom Auto 1"
```
Чтобы просмотреть сведения о пространстве имен и подключенных клиентах, введите одно из следующих действий:
- Windows Server 2008: `wdsutil /Get-Namespace /Server:MyWDSServer /Namespace:"Custom Auto 1" /Show:Clients`
- Windows Server 2008 R2: `wdsutil /Get-Namespace /Server:MyWDSServer /Namespace:"Custom Auto 1" /details:Clients`
  #### <a name="additional-references"></a>Дополнительные ссылки
  [Синтаксис командной строки](command-line-syntax-key.md)
  [с помощью команды get-аллнамеспацес](using-the-get-allnamespaces-command.md)
   с[помощью команды New-Namespace](using-the-new-namespace-command.md)
  [с помощью команды Remove-Namespace,](using-the-remove-namespace-command.md)
  [: Start-Namespace.](subcommand-start-namespace.md)
