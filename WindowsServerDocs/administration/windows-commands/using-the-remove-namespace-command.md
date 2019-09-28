---
title: Использование команды Remove-Namespace
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: b4c087442c43fd885fe4554cb29f9b2788420e05
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71362791"
---
# <a name="using-the-remove-namespace-command"></a>Использование команды Remove-Namespace

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет пользовательское пространство имен.
## <a name="syntax"></a>Синтаксис
```
wdsutil /remove-Namespace /Namespace:<Namespace name> [/Server:<Server name>] [/force]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/Namespace: <Namespace name>|Указывает имя пространства имен. Это не понятное имя, оно должно быть уникальным.<br /><br />**служба роли сервера развертывания**-   : Синтаксис имени пространства имен —/namespace: WDS: <ImageGroup> @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4. Пример: **WDS: ImageGroup1/install. wim/1**<br />**служба роли транспортного сервера**-   : Это значение должно совпадать с именем, присвоенным пространству имен при его создании на сервере.|
|[/Server: <Server name>]|Указывает имя сервера. Это может быть NetBIOS-имя или полное доменное имя (FQDN). Если имя сервера не указано, используется локальный сервер.|
|/Force|немедленно удаляет пространство имен и завершает работу всех клиентов. Обратите внимание, что если не указать **/Force**, существующие клиенты могут завершить перенос, но новые клиенты не смогут присоединиться.|
## <a name="BKMK_examples"></a>Примеров
Чтобы присвоить пространство имен (текущие клиенты могут завершить процесс перемещения, но новые клиенты не смогут присоединиться), введите:
```
wdsutil /remove-Namespace /Namespace:"Custom Auto 1"
```
Для принудительного завершения работы всех клиентов введите:
```
wdsutil /remove-Namespace /Server:MyWDSServer /Namespace:"Custom Auto 1" /force
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды get-аллнамеспацес](using-the-get-allnamespaces-command.md)
[с помощью команды New-Namespace](using-the-new-namespace-command.md)
[подкоманда: Start-Namespace](subcommand-start-namespace.md)
