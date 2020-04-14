---
title: SC Delete
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2fe94fb3-e4d1-47b5-b999-39995ecbb644
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 05b276de04d4250cc03e4b2976bf8c1330ef82ce
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80835387"
---
# <a name="sc-delete"></a>SC Delete



Удаляет подраздел службы из реестра. Если служба запущена или другой процесс имеет открытый обработчик, служба помечается для удаления.

В разделе [Примеры](#examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
sc [<ServerName>] delete [<ServiceName>]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<ServerName >|Указывает имя удаленного сервера, на котором расположена служба. Имя должно использовать формат UNC (например, \\\\MyServer). Чтобы запустить SC. exe локально, опустите этот параметр.|
|\<ServiceName >|Указывает имя службы, возвращенное операцией **жеткэйнаме** .|
|?|Отображает справку в командной строке.|

## <a name="remarks"></a>Примечания

Используйте оснастку " **Установка и удаление программ** " на **панели управления** для удаления DHCP, DNS или любых других встроенных служб операционной системы. Обратите внимание, что компонент " **Установка и удаление программ** " не только удаляет подраздел реестра для службы, но также удаляет службу и все ярлыки.

## <a name="examples"></a>Примеры

Чтобы удалить подраздел Service **невсерв** из реестра на локальном компьютере, введите:
```
sc delete newserv
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)