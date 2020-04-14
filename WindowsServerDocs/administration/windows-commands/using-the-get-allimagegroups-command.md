---
title: Get-Аллимажеграупс
description: Раздел команд Windows для Get-Аллимажеграупс, который извлекает сведения обо всех группах образов на сервере и всех образах в этих группах образов.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2ca06533-bcf5-4590-ac8e-263d6c9874f8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 19285422612f8be34d39e6152fcf0300e1919b8a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80831334"
---
# <a name="get-allimagegroups"></a>Get-Аллимажеграупс

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Извлекает сведения обо всех группах образов на сервере и всех образах в этих группах образов.

## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Get-AllImageGroups [/Server:<Server name>] [/detailed]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server:<Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
|[/детаилед]|Возвращает метаданные изображения из каждого изображения. Если этот параметр не используется, поведение по умолчанию — возврат только имени, описания и имени файла для каждого образа.|
## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы просмотреть сведения о группах образов, введите одно из следующих действий:
```
wdsutil /Get-AllImageGroups
wdsutil /verbose /Get-AllImageGroups /Server:MyWDSServer /detailed
```
## <a name="additional-references"></a>Дополнительные материалы
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[помощью команды Add-Имажеграуп](using-the-add-imagegroup-command.md) ,
[помощью команды Get-имажеграуп](using-the-get-imagegroup-command.md) ,
[с помощью команды Remove-имажеграуп,](using-the-remove-imagegroup-command.md)
[подкоманде: Set-имажеграуп](subcommand-set-imagegroup.md)
