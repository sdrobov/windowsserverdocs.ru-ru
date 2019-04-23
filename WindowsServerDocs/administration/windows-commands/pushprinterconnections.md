---
title: pushprinterconnections
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c30afb97-b149-478f-a4b9-2cbc25361818 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c571d3adffd0e6a28f63f6d821b2524dc055aa9a
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59873725"
---
# <a name="pushprinterconnections"></a>pushprinterconnections



Считывает параметры развертывания подключения принтера из групповой политики и развертывает и удаляет подключения принтеров при необходимости.

## <a name="syntax"></a>Синтаксис

```
pushprinterconnections <-log> <-?>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|<-log>|Записывает в файл журнала отладки пользователя для % temp или записи в журнал отладки машины % windir%\temp.|
|<-?>|Отображает справку в командной строке.|

## <a name="remarks"></a>Примечания

Эта программа предназначена для использования в сценарии входа в систему компьютера запуска или пользователя и не должны выполняться из командной строки.

#### <a name="additional-references"></a>Дополнительная справка

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)
-   [Развертывание принтеров с помощью групповой политики](https://go.microsoft.com/fwlink/?LinkId=230627)