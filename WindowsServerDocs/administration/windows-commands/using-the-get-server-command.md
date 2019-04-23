---
title: С помощью команды get сервера
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bef60db4-d58d-4304-ab4b-be53dd3271c3
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: da8bf0fc6e31bd8d0079933f1d7c529c4fe96f42
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59870985"
---
# <a name="using-the-get-server-command"></a>С помощью команды get сервера

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Извлекает сведения из указанного сервера служб развертывания Windows.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Get-Server [/Server:<Server name>] /Show:{Config | Images | All} [/detailed]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, используется локальный сервер.|
|/Show:{Config &#124; Images &#124; All}|Указывает тип возвращаемых сведений.<br /><br />-   **Config** возвращает сведения о конфигурации.<br />-   **Образы** возвращает сведения о групп образов, образов загрузки и образов установки.<br />-   **Все** возвращает сведения о конфигурации и сведения об образе.|
|[/ подробные]|Можно использовать этот параметр вместе с **/Show:Images** или **/Show:All** для указания, что все метаданные изображения из каждого образа должны быть возвращены. Если **/ подробные** параметр не указан, по умолчанию задается для возврата имени образа, описание и имя файла.|
## <a name="BKMK_examples"></a>Примеры
Чтобы просмотреть сведения о сервере, введите следующую команду:
```
wdsutil /Get-Server /Show:Config
```
Чтобы просмотреть подробные сведения о сервере, введите:
```
wdsutil /verbose /Get-Server /Server:MyWDSServer /Show:All /detailed
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды отключения сервера](using-the-disable-server-command.md)
[с помощью команды enable-Server](using-the-enable-server-command.md)
[Using Команды Initialize-Server](using-the-initialize-server-command.md)
[подкоманда: set-Server](subcommand-set-server.md)
[подкоманда: запустить сервер](subcommand-start-server.md) 
 [ Подкоманда: stop-Server](subcommand-stop-server.md)
[параметр uninitialize сервера](the-uninitialize-server-option.md)
