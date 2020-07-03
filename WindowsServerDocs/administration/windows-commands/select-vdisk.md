---
title: select vdisk
description: Справочная статья для * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8808872a-3523-4205-a6c6-83fa738ee37a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 734b31d9c9bcf174bf4617418978935bc49ad6da
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85936437"
---
# <a name="select-vdisk"></a>select vdisk

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

выбирает указанный виртуальный жесткий диск виртуального жесткого диска \( \) и перемещает фокус на него.

> [!NOTE]
> Эта команда применима только к Windows 7 и Windows Server 2008 R2.

## <a name="syntax"></a>Синтаксис

```
select vdisk file=<full path> [noerr]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------|--------|
|File\=<full path>|Указывает полный путь и имя существующего файла виртуального жесткого диска.|
|Noerr|Используется только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки.|

## <a name="examples"></a>Примеры
Чтобы переместить фокус на виртуальный жесткий диск с именем Test. VHD, введите:

```
select vdisk file=c:\test\test.vhd
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

-   [подключить виртуальный диск](attach-vdisk.md)

-   [compact vdisk](compact-vdisk.md)



-   [Отсоединить виртуальный диск](detach-vdisk.md)

-   [detail vdisk](detail-vdisk.md)

-   [expand vdisk](expand-vdisk.md)

-   [Слияние VDISK](merge-vdisk.md)

-   [list_1](list_1.md)


