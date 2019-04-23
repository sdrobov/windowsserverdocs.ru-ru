---
title: С помощью команды remove-пространство имен
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4eb758b6-8519-4e26-9fe0-2e19bb0e8702
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 115c0a90a60e18ee4b89758200773d1dfec2163f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59842045"
---
# <a name="using-the-remove-namespace-command"></a>С помощью команды remove-пространство имен

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаление пользовательского пространства имен.
## <a name="syntax"></a>Синтаксис
```
wdsutil /remove-Namespace /Namespace:<Namespace name> [/Server:<Server name>] [/force]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/ Пространство имен:<Namespace name>|Задает имя пространства имен. Понятное имя, и оно должно быть уникальным.<br /><br />-   **Служба роли сервера развертывания**: Синтаксис имени пространства имен: /Namespace:WDS:<ImageGroup>/<ImageName>/<Index>. Пример: **WDS:ImageGroup1/Install.wim/1**<br />-   **Служба роли сервера транспорта**: Это значение должно соответствовать имя, присвоенное пространство имен, если он был создан на сервере.|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, используется локальный сервер.|
|[/ force]|немедленно удаляет пространство имен и завершает выполнение всех клиентов. Обратите внимание, что, если не указано **/force**, существующие клиенты могут выполнить передачу, но новые клиенты не смогут присоединиться.|
## <a name="BKMK_examples"></a>Примеры
Чтобы остановить пространства имен (текущих клиентов можно выполнить передачу, но новые клиенты не смогут присоединиться к), тип:
```
wdsutil /remove-Namespace /Namespace:"Custom Auto 1"
```
Чтобы выполнить завершение всех клиентов, введите следующую команду:
```
wdsutil /remove-Namespace /Server:MyWDSServer /Namespace:"Custom Auto 1" /force
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды get-AllNamespaces](using-the-get-allnamespaces-command.md)
[с помощью команды новое пространство имен](using-the-new-namespace-command.md) 
 [ Подкоманда: start-пространство имен](subcommand-start-namespace.md)
