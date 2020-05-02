---
title: Get-Server
description: Справочный раздел по Get-Server, который извлекает сведения с указанного сервера служб развертывания Windows.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bef60db4-d58d-4304-ab4b-be53dd3271c3
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a760371797af8eb95da386a3a5b9dbb0dcf7ba3c
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719740"
---
# <a name="get-server"></a>Get-Server

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Извлекает сведения с указанного сервера служб развертывания Windows.

## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Get-Server [/Server:<Server name>] /Show:{Config | Images | All} [/detailed]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть NetBIOS-имя или полное доменное имя (FQDN). Если имя сервера не указано, используется локальный сервер.|
|/Show: {config &#124; Images &#124; ALL}|Указывает тип возвращаемых данных.<p>-   **Config** возвращает сведения о конфигурации.<br />-   **Изображения** возвращают сведения о группах образов, загрузочных образах и образах установки.<br />-   **ALL** возвращает сведения о конфигурации и сведения об образе.|
|[/детаилед]|Этот параметр можно использовать с **/Show: Images** или **/Show: ALL** , чтобы указать, что должны возвращаться все метаданные образа из каждого изображения. Если параметр **/детаилед** не используется, по умолчанию возвращается имя образа, описание и имя файла.|
## <a name="examples"></a>Примеры
Чтобы просмотреть сведения о сервере, введите:
```
wdsutil /Get-Server /Show:Config
```
Чтобы просмотреть подробные сведения о сервере, введите:
```
wdsutil /verbose /Get-Server /Server:MyWDSServer /Show:All /detailed
```
## <a name="additional-references"></a>Дополнительные ссылки
- [Синтаксис](command-line-syntax-key.md)
командной строки[с помощью](using-the-disable-server-command.md)
команды "Disable-Server" с помощью команды "[Enable](using-the-enable-server-command.md)
-Server" с использованием подкоманды[Initialize](using-the-initialize-server-command.md)
-Server[: Set-](subcommand-set-server.md)
Server подкоманда:[Start-](subcommand-start-server.md)
Server подкоманда[: "-Server](subcommand-stop-server.md)
["-"параметр отмены инициализации](the-uninitialize-server-option.md)
