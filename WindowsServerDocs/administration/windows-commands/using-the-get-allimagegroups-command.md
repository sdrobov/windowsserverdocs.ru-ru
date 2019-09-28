---
title: Использование команды Get-Аллимажеграупс
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 54e302dca5014d084c7277154eb491f9e33a536b
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71363312"
---
# <a name="using-the-get-allimagegroups-command"></a>Использование команды Get-Аллимажеграупс

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Извлекает сведения обо всех группах образов на сервере и всех образах в этих группах образов.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Get-AllImageGroups [/Server:<Server name>] [/detailed]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/Server: <Server name>]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|
|[/детаилед]|Возвращает метаданные изображения из каждого изображения. Если этот параметр не используется, поведение по умолчанию — возврат только имени, описания и имени файла для каждого образа.|
## <a name="BKMK_examples"></a>Примеров
Чтобы просмотреть сведения о группах образов, введите одно из следующих действий:
```
wdsutil /Get-AllImageGroups
wdsutil /verbose /Get-AllImageGroups /Server:MyWDSServer /detailed
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды add-имажеграуп](using-the-add-imagegroup-command.md)
 с[помощью команды Get-Имажеграуп](using-the-get-imagegroup-command.md)
[с помощью команды Remove-Имажеграуп](using-the-remove-imagegroup-command.md)
[: Set-имажеграуп](subcommand-set-imagegroup.md)
