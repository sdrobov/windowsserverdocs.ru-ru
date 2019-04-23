---
title: С помощью команды get-пространство имен
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: bd11880b6e733850b522c3a06152ac7ce7a28841
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59889665"
---
# <a name="using-the-get-namespace-command"></a>С помощью команды get-пространство имен

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает сведения о пользовательского пространства имен.
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
|Параметр|Описание|
|-------|--------|
|/ Пространство имен:<Namespace name>|Задает имя пространства имен. Обратите внимание, что это не понятное имя, и оно должно быть уникальным.<br /><br />-Сервер развертывания: Синтаксис имени пространства имен: /Namspace:WDS:<ImageGroup>/<ImageName>/<Index>. Пример: **WDS:ImageGroup1/Install.wim/1**<br />-Транспортный сервер: Это значение должно соответствовать имени, данное пространство имен при его создании на сервере.|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, используется локальный сервер.|
|[/ Show: клиенты] или [/ сведения: клиенты]|Отображает сведения о клиентских компьютерах, подключенных к указанным пространством имен.|
## <a name="BKMK_examples"></a>Примеры
Чтобы просмотреть сведения о пространстве имен, введите:
```
wdsutil /Get-Namespace /Namespace:"Custom Auto 1"
```
Чтобы просмотреть сведения о пространстве имен и клиентов, которые подключены, введите одно из следующих:
-   Windows Server 2008: `wdsutil /Get-Namespace /Server:MyWDSServer /Namespace:"Custom Auto 1" /Show:Clients`
-   Windows Server 2008 R2: `wdsutil /Get-Namespace /Server:MyWDSServer /Namespace:"Custom Auto 1" /details:Clients`
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды get-AllNamespaces](using-the-get-allnamespaces-command.md)
[с помощью команды новое пространство имен](using-the-new-namespace-command.md)
[Using Команда remove-Namespace](using-the-remove-namespace-command.md)
[подкоманда: start-пространство имен](subcommand-start-namespace.md)
