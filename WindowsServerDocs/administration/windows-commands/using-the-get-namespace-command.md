---
title: Get — Namespace
description: Справочная статья по Get-Namespace, в которой отображаются сведения о пользовательском пространстве имен.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ea641bab-e97b-4909-918e-447730027dc1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a029d56b2aea0a05bb12121cde89a1a731f3e4c5
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85932189"
---
# <a name="get-namespace"></a>Get — Namespace

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает сведения о пользовательском пространстве имен.

## <a name="syntax"></a>Синтаксис
Windows Server 2008 R2
```
wdsutil /Get-Namespace /Namespace:<Namespace name> [/Server:<Server name>] [/Show:Clients]
```
Windows Server 2008 R2
```
wdsutil /Get-Namespace /Namespace:<Namespace name> [/Server:<Server name>] [/details:Clients]
```
### <a name="parameters"></a>Параметры

|               Параметр               |                                                                                                                                                                                         Описание                                                                                                                                                                                          |
|---------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      Имен<Namespace name>      | Указывает имя пространства имен. Обратите внимание, что это не понятное имя, оно должно быть уникальным.<p>-Сервер развертывания. синтаксис имени пространства имен —/Намспаце: WDS: <ImageGroup> / <ImageName> / <Index> . Например: **WDS: ImageGroup1/install. wim/1**<br />— Транспортный сервер. это значение должно совпадать с именем, присвоенным пространству имен при его создании на сервере. |
|        [/Server: <Server name> ]        |                                                                                                             Указывает имя сервера. Это может быть NetBIOS-имя или полное доменное имя (FQDN). Если имя сервера не указано, используется локальный сервер.                                                                                                              |
| [/Show: Clients] или [/детаилс: Clients] |                                                                                                                                                  Отображает сведения о клиентских компьютерах, подключенных к указанному пространству имен.                                                                                                                                                  |

## <a name="examples"></a>Примеры
Чтобы просмотреть сведения о пространстве имен, введите:
```
wdsutil /Get-Namespace /Namespace:Custom Auto 1
```
Чтобы просмотреть сведения о пространстве имен и подключенных клиентах, введите одно из следующих действий:
- Windows Server 2008:`wdsutil /Get-Namespace /Server:MyWDSServer /Namespace:Custom Auto 1 /Show:Clients`
- Windows Server 2008 R2:`wdsutil /Get-Namespace /Server:MyWDSServer /Namespace:Custom Auto 1 /details:Clients`
  ## <a name="additional-references"></a>Дополнительные ссылки
  - Ключ синтаксиса [командной строки](command-line-syntax-key.md) 
   [Использование команды](using-the-get-allnamespaces-command.md) 
   Get-аллнамеспацес [Использование команды](using-the-new-namespace-command.md) 
   New-Namespace [Использование команды](using-the-remove-namespace-command.md) 
   Remove-Namespace [Подкоманда: Start-Namespace](subcommand-start-namespace.md)
