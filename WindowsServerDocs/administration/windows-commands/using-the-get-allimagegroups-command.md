---
title: С помощью команды get-AllImageGroups
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2ca06533-bcf5-4590-ac8e-263d6c9874f8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 917f61327a3d39ee97c5fd59072884f7844c487e
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59822355"
---
# <a name="using-the-get-allimagegroups-command"></a>С помощью команды get-AllImageGroups

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Извлекает сведения о всех групп образов на сервере и все образы в этих групп образов.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Get-AllImageGroups [/Server:<Server name>] [/detailed]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, будет использоваться локальный сервер.|
|[/ подробные]|Возвращает метаданные изображения из каждого изображения. Если этот параметр не указан, по умолчанию задается для возврата только имя образа, описание и имя файла для каждого образа.|
## <a name="BKMK_examples"></a>Примеры
Чтобы просмотреть сведения о группах образ, введите одно из следующих:
```
wdsutil /Get-AllImageGroups
wdsutil /verbose /Get-AllImageGroups /Server:MyWDSServer /detailed
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды add-ImageGroup](using-the-add-imagegroup-command.md)
[с помощью команды get-ImageGroup](using-the-get-imagegroup-command.md)
[Using Команда Remove-ImageGroup](using-the-remove-imagegroup-command.md)
[подкоманда: set-ImageGroup](subcommand-set-imagegroup.md)
