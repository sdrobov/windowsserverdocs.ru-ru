---
title: Подкоманды start-пространство имен
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2dd1c11e-6ab7-4129-9e3a-3f80e0ba59c0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5dc484a3b159cd510d7a61484f4f46b1f1db7a4e
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59877135"
---
# <a name="subcommand-start-namespace"></a>Подкоманда: start-пространство имен

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 запускает пространство имен рассылкой по расписанию.
## <a name="syntax"></a>Синтаксис
```
wdsutil /start-Namespace /Namespace:<Namespace name> [/Server:<Server name>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/ Пространство имен:<Namespace name>|Задает имя пространства имен. Обратите внимание, что это не понятное имя, и оно должно быть уникальным.<br /><br />-   **Сервер развертывания**: Синтаксис имени пространства имен: /Namspace:WDS:<Image group>/<Image name>/<Index>. Пример: **WDS:ImageGroup1/Install.wim/1**<br />-   **Транспортный сервер**: Это имя должно соответствовать имени, данное пространство имен при его создании на сервере.|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, будет использоваться локальный сервер.|
## <a name="BKMK_examples"></a>Примеры
Чтобы запустить пространство имен, введите одно из следующих:
```
wdsutil /start-Namespace /Namespace:"Custom Auto 1"
wdsutil /start-Namespace /Server:MyWDSServer /Namespace:"Custom Auto 1"
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды get-AllNamespaces](using-the-get-allnamespaces-command.md)
[с помощью команды новое пространство имен](using-the-new-namespace-command.md)
[Using Команда remove-пространство имен](using-the-remove-namespace-command.md)
