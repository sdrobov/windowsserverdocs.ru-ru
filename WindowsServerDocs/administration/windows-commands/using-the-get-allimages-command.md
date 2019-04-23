---
title: С помощью команды get-AllImages
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 57b81dd3dd3a24876c4401e80d08130ed5243888
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59872565"
---
# <a name="using-the-get-allimages-command"></a>С помощью команды get-AllImages

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Извлекает сведения о всех образов на сервере.
## <a name="syntax"></a>Синтаксис
```
wdsutil /Get-AllImages [/Server:<Server name>] /Show:{Boot | Install | LegacyRis | All} [/detailed]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, будет использоваться локальный сервер.|
|/ Показать: {загрузки &#124; установить &#124; LegacyRis &#124; все}|-   **Загрузки** возвращает только образы загрузки.<br />-   **Установка** возвращает установки образов, а также сведения о групп образов, содержащих их.<br />-   **LegacyRis** возвращает только образы на удаленной установки (RIS).<br />-   **Все** возвращает загрузку информации об изображении, сведениями об установке образа (в том числе сведения о группах образ) и сведения об образе RIS.|
|[/ подробные]|Указывает, что все метаданные изображения из каждого образа должны быть возвращены. Если данный параметр не указан, по умолчанию задается для возврата только имя образа, описание и имя файла.|
## <a name="BKMK_examples"></a>Примеры
Чтобы просмотреть сведения об образах, введите одно из следующих:
```
wdsutil /Get-AllImages /Show:Install
wdsutil /verbose /Get-AllImages /Server:MyWDSServer /Show:All /detailed
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды add образа](using-the-add-image-command.md)
[с помощью команды копирования образа](using-the-copy-image-command.md)
[Using Команда export-Image](using-the-export-image-command.md)
[с помощью команды remove образа](using-the-remove-image-command.md)
[с помощью команды заменить изображение](using-the-replace-image-command.md) 
 [Подкоманда: set-Image](subcommand-set-image.md)
