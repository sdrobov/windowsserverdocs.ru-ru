---
title: Подкоманда Start — пространство имен
description: Команда Windows для подкоманды Start-Namespace, которая запускает пространство имен, запланированное для приведения.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2dd1c11e-6ab7-4129-9e3a-3f80e0ba59c0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1a30220f78d5ae865095149fc7170a6ce9b8fb1b
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80833767"
---
# <a name="subcommand-start-namespace"></a>Подкоманда: Start-Namespace

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Запускает пространство имен, запланированное для приведения.

## <a name="syntax"></a>Синтаксис
```
wdsutil /start-Namespace /Namespace:<Namespace name[/Server:<Server name>]
```
### <a name="parameters"></a>Параметры

|          Параметр          |                                                                                                                                                                                             Описание                                                                                                                                                                                             |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /Namespace: < имя пространства имен| Указывает имя пространства имен. Обратите внимание, что это не понятное имя, оно должно быть уникальным.<p>**сервер развертывания**-   . синтаксис имени пространства имен —/НАМСПАЦЕ: WDS:<Image group>/<Image name>/<Index>. Например: **WDS: ImageGroup1/install. wim/1**<br />-   **транспортный сервер**: это имя должно совпадать с именем, присвоенным пространству имен при создании на сервере. |
|   [/Server:<Server name>]   |                                                                                                           Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.                                                                                                           |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы запустить пространство имен, введите одно из следующих действий:
```
wdsutil /start-Namespace /Namespace:Custom Auto 1
wdsutil /start-Namespace /Server:MyWDSServer /Namespace:Custom Auto 1
```
## <a name="additional-references"></a>Дополнительные материалы
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды Get-Аллнамеспацес,](using-the-get-allnamespaces-command.md)
[помощью команды New-Namespace](using-the-new-namespace-command.md)
[помощью команды Remove-Namespace](using-the-remove-namespace-command.md) .
