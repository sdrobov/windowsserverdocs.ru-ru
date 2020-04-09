---
title: Get-Server
description: Раздел команд Windows для Get-Server, который извлекает сведения с указанного сервера служб развертывания Windows.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bef60db4-d58d-4304-ab4b-be53dd3271c3
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 65903dc89730eb9d1da23be31ecc1909daece9c4
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80830847"
---
# <a name="get-server"></a>Get-Server

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Извлекает сведения с указанного сервера служб развертывания Windows.

## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Get-Server [/Server:<Server name>] /Show:{Config | Images | All} [/detailed]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть NetBIOS-имя или полное доменное имя (FQDN). Если имя сервера не указано, используется локальный сервер.|
|/Show: {config &#124; Images &#124; ALL}|Указывает тип возвращаемых данных.<p>-   **config** возвращает сведения о конфигурации.<br />-   **образы** возвращают сведения о группах образов, загрузочных образах и образах установки.<br />-   **все** возвращает сведения о конфигурации и сведения об образе.|
|[/детаилед]|Этот параметр можно использовать с **/Show: Images** или **/Show: ALL** , чтобы указать, что должны возвращаться все метаданные образа из каждого изображения. Если параметр **/детаилед** не используется, по умолчанию возвращается имя образа, описание и имя файла.|
## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы просмотреть сведения о сервере, введите:
```
wdsutil /Get-Server /Show:Config
```
Чтобы просмотреть подробные сведения о сервере, введите:
```
wdsutil /verbose /Get-Server /Server:MyWDSServer /Show:All /detailed
```
## <a name="additional-references"></a>Дополнительные материалы
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды "Disable-Server"](using-the-disable-server-command.md)
[с помощью команды Enable](using-the-enable-server-command.md) -Server
при [помощи команды "инициализировать-Server command](using-the-initialize-server-command.md)
": [Set-](subcommand-set-server.md) Server
подкоманда: [Start-](subcommand-start-server.md) Server
[подкоманда:-Server](subcommand-stop-server.md)
[параметром Uninitialize-Server](the-uninitialize-server-option.md)
