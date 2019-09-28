---
title: Подкоманда Start — пространство имен
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 55fe4a6136fe4f8e886dc62fff746a1e5ff1898f
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71370746"
---
# <a name="subcommand-start-namespace"></a>Подкоманда: Start-Namespace

> Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 запускает пространство имен, запланированное для приведения.
> ## <a name="syntax"></a>Синтаксис
> ```
> wdsutil /start-Namespace /Namespace:<Namespace name> [/Server:<Server name>]
> ```
> ## <a name="parameters"></a>Параметры
> 
> |          Параметр          |                                                                                                                                                                                             Описание                                                                                                                                                                                             |
> |-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
> | /Namespace: <Namespace name> | Указывает имя пространства имен. Обратите внимание, что это не понятное имя, оно должно быть уникальным.<br /><br />**сервер развертывания**-   : Синтаксис имени пространства имен —/Намспаце: WDS: <Image group> @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4. Пример: **WDS: ImageGroup1/install. wim/1**<br />**транспортный сервер**-   : Это имя должно совпадать с именем, присвоенным пространству имен при его создании на сервере. |
> |   [/Server: <Server name>]   |                                                                                                           Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.                                                                                                           |
> 
> ## <a name="BKMK_examples"></a>Примеров
> Чтобы запустить пространство имен, введите одно из следующих действий:
> ```
> wdsutil /start-Namespace /Namespace:"Custom Auto 1"
> wdsutil /start-Namespace /Server:MyWDSServer /Namespace:"Custom Auto 1"
> ```
> #### <a name="additional-references"></a>Дополнительные ссылки
> [Ключ синтаксиса командной строки](command-line-syntax-key.md)
> [с помощью команды get-аллнамеспацес](using-the-get-allnamespaces-command.md)
> [с помощью команды New-Namespace](using-the-new-namespace-command.md)
> [с помощью команды Remove-Namespace](using-the-remove-namespace-command.md) .
