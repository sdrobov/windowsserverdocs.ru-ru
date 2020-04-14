---
title: Get-Аллимажес
description: Раздел команд Windows для Get-Аллимажес, который извлекает сведения обо всех образах на сервере.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 19de3720-4315-415a-8dc6-486caa0b2100
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f1358d7ae4a86b6439b9a304e10e3aa569112d5a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80831307"
---
# <a name="get-allimages"></a>Get-Аллимажес

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Извлекает сведения обо всех образах на сервере.

## <a name="syntax"></a>Синтаксис
```
wdsutil /Get-AllImages [/Server:<Server name>] /Show:{Boot | Install | LegacyRis | All} [/detailed]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
|/Show: { &#124; установка &#124; легацирис &#124; все}|-   ная **Загрузка** возвращает только загрузочные образы.<br />-   **Install** возвращает образы установки, а также сведения о группах образов, содержащих их.<br />-   **легацирис** возвращает только образы служб удаленной установки (RIS).<br />-   **все** возвращает сведения об образе загрузки, сведения об образе установки (включая сведения о группах образов) и сведения об образе RIS.|
|[/детаилед]|Указывает, что должны возвращаться все метаданные изображения из каждого изображения. Если этот параметр не используется, поведение по умолчанию — возврат только имени, описания и имени файла изображения.|
## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы просмотреть сведения об образах, введите одно из следующих действий:
```
wdsutil /Get-AllImages /Show:Install
wdsutil /verbose /Get-AllImages /Server:MyWDSServer /Show:All /detailed
```
## <a name="additional-references"></a>Дополнительные материалы
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[Использование команды add-Image](using-the-add-image-command.md)
[помощью команды Copy-](using-the-copy-image-command.md) Image
с помощью команды [reexport-](using-the-export-image-command.md) Image
[помощью команды Remove](using-the-remove-image-command.md) -image,
[с помощью команды replace-](using-the-replace-image-command.md) Image
[подкоманде: Set-Image.](subcommand-set-image.md)
