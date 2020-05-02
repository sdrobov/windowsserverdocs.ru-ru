---
title: Get-Аллимажес
description: Справочный раздел по Get-Аллимажес, который извлекает сведения обо всех изображениях на сервере.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 19de3720-4315-415a-8dc6-486caa0b2100
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c1f32a1789b22d04b7b61979d0ea49d91f0cf157
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720018"
---
# <a name="get-allimages"></a>Get-Аллимажес

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Извлекает сведения обо всех образах на сервере.

## <a name="syntax"></a>Синтаксис
```
wdsutil /Get-AllImages [/Server:<Server name>] /Show:{Boot | Install | LegacyRis | All} [/detailed]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
|/Show: {Загрузка &#124; установка &#124; Легацирис &#124; все}|-   **Boot** возвращает только загрузочные образы.<br />-   **Install** возвращает образы установки, а также сведения о группах образов, содержащих их.<br />-   **Легацирис** возвращает только образы служб удаленной установки (RIS).<br />-   **Все** возвращает сведения об образе загрузки, сведения об образе установки (включая сведения о группах образов) и сведения об образе RIS.|
|[/детаилед]|Указывает, что должны возвращаться все метаданные изображения из каждого изображения. Если этот параметр не используется, поведение по умолчанию — возврат только имени, описания и имени файла изображения.|
## <a name="examples"></a>Примеры
Чтобы просмотреть сведения об образах, введите одно из следующих действий:
```
wdsutil /Get-AllImages /Show:Install
wdsutil /verbose /Get-AllImages /Server:MyWDSServer /Show:All /detailed
```
## <a name="additional-references"></a>Дополнительные ссылки
- [Ключ](command-line-syntax-key.md)
синтаксиса командной строки[с помощью команды Add-](using-the-add-image-command.md)
Image с помощью команды "[Копировать](using-the-copy-image-command.md)
изображение" с помощью команды "[Export](using-the-export-image-command.md)
-Image" с помощью команды[Remove](using-the-remove-image-command.md)
-Image с помощью команды[Replace](using-the-replace-image-command.md)
-Image[: Set-Image](subcommand-set-image.md)
