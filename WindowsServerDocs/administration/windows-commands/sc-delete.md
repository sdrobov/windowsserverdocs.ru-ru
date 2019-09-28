---
title: SC Delete
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2fe94fb3-e4d1-47b5-b999-39995ecbb644
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ad64d0f7c772b8d29a191b5f3e690d74c8765717
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71371278"
---
# <a name="sc-delete"></a>SC Delete



Удаляет подраздел службы из реестра. Если служба запущена или другой процесс имеет открытый обработчик, служба помечается для удаления.

В разделе [Примеры](#examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
sc [<ServerName>] delete [<ServiceName>]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|@no__t 0ServerName >|Указывает имя удаленного сервера, на котором расположена служба. Имя должно использовать формат UNC (например, \\ @ no__t-1myserver). Чтобы запустить SC. exe локально, опустите этот параметр.|
|@no__t 0ServiceName >|Указывает имя службы, возвращенное операцией **жеткэйнаме** .|
|?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

Используйте оснастку " **Установка и удаление программ** " на **панели управления** для удаления DHCP, DNS или любых других встроенных служб операционной системы. Обратите внимание, что компонент " **Установка и удаление программ** " не только удаляет подраздел реестра для службы, но также удаляет службу и все ярлыки.

## <a name="examples"></a>Примеры

Чтобы удалить подраздел Service **невсерв** из реестра на локальном компьютере, введите:
```
sc delete newserv
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)