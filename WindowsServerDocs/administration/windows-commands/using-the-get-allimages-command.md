---
title: Использование команды Get-Аллимажес
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 19de3720-4315-415a-8dc6-486caa0b2100
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5122a5660031d503795715c0005b404f910d6626
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71363501"
---
# <a name="using-the-get-allimages-command"></a>Использование команды Get-Аллимажес

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Извлекает сведения обо всех образах на сервере.
## <a name="syntax"></a>Синтаксис
```
wdsutil /Get-AllImages [/Server:<Server name>] /Show:{Boot | Install | LegacyRis | All} [/detailed]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server: <Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
|/Show: { &#124; установка &#124; легацирис &#124; все}|-   **Загрузка** возвращает только загрузочные образы.<br />-   .**Установка** возвращает образы установки, а также сведения о группах образов, содержащих их.<br />-   **легацирис** возвращает только образы служб удаленной установки (RIS).<br />-   **ALL** возвращает сведения об образе загрузки, сведения об образе установки (включая сведения о группах образов) и сведения об образе RIS.|
|[/детаилед]|Указывает, что должны возвращаться все метаданные изображения из каждого изображения. Если этот параметр не используется, поведение по умолчанию — возврат только имени, описания и имени файла изображения.|
## <a name="BKMK_examples"></a>Примеров
Чтобы просмотреть сведения об образах, введите одно из следующих действий:
```
wdsutil /Get-AllImages /Show:Install
wdsutil /verbose /Get-AllImages /Server:MyWDSServer /Show:All /detailed
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Синтаксис командной строки](command-line-syntax-key.md)
[с помощью команды add-Image](using-the-add-image-command.md)
 с помощью команды[Copy-](using-the-copy-image-command.md)Image @no__t[-5 с помощью команды](using-the-export-image-command.md)Remove-Image, 
 с помощью[команды Удалить изображение](using-the-remove-image-command.md)@no__t[-9 с помощью Команда Replace-Image](using-the-replace-image-command.md)1[подкоманда: Set-Image](subcommand-set-image.md)
