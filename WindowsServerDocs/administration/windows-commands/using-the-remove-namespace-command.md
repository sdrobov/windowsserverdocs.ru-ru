---
title: Remove-Namespace
description: Раздел команд Windows для Remove-Namespace, который удаляет пользовательское пространство имен.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4eb758b6-8519-4e26-9fe0-2e19bb0e8702
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1f8b830a5d99d13ed00a3a19f2cf246ad71d1c5f
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80830237"
---
# <a name="using-the-remove-namespace-command"></a>Использование команды Remove-Namespace

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет пользовательское пространство имен.

## <a name="syntax"></a>Синтаксис
```
wdsutil /remove-Namespace /Namespace:<Namespace name> [/Server:<Server name>] [/force]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/Namespace:<Namespace name>|Указывает имя пространства имен. Это не понятное имя, оно должно быть уникальным.<p>**служба роли сервера развертывания**-   . синтаксис имени пространства имен:/namespace: WDS:<ImageGroup>/<ImageName>/<Index>. Например: **WDS: ImageGroup1/install. wim/1**<br />**служба роли транспортного сервера**-   . это значение должно совпадать с именем, присвоенным пространству имен при его создании на сервере.|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть NetBIOS-имя или полное доменное имя (FQDN). Если имя сервера не указано, используется локальный сервер.|
|/Force|немедленно удаляет пространство имен и завершает работу всех клиентов. Обратите внимание, что если не указать **/Force**, существующие клиенты могут завершить перенос, но новые клиенты не смогут присоединиться.|
## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы присвоить пространство имен (текущие клиенты могут завершить процесс перемещения, но новые клиенты не смогут присоединиться), введите:
```
wdsutil /remove-Namespace /Namespace:Custom Auto 1
```
Для принудительного завершения работы всех клиентов введите:
```
wdsutil /remove-Namespace /Server:MyWDSServer /Namespace:Custom Auto 1 /force
```
## <a name="additional-references"></a>Дополнительные материалы
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды Get-Аллнамеспацес,](using-the-get-allnamespaces-command.md)
[с помощью команды New-Namespace](using-the-new-namespace-command.md)
[подкоманде: Start-Namespace](subcommand-start-namespace.md)
