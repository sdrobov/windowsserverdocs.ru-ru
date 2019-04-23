---
title: pnputil
description: Сведения об управлении хранилище драйверов с помощью служебной программы pnputil.exe.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fab686b8-09d3-4f6c-afa2-630e6036f44c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: 5bde78d97be8def9f8594572869c34ef213db480
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59862545"
---
# <a name="pnputil"></a>pnputil

PnPUtil.exe — это служебная программа командной строки, который можно использовать для управления хранилище драйверов. Pnputil можно использовать для добавления пакетов драйверов, удаление пакетов драйверов и списка пакетов драйверов, которые находятся в хранилище.

## <a name="syntax"></a>Синтаксис

```
pnputil.exe [-f | -i] [ -? | -a | -d | -e ] <INF name>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|-a|Указывает, чтобы добавить файл INF.|
|-d|Задает удаление конкретного файла INF.|
|-e|Задает для перечисления всех файлов INF независимых производителей.|
|-f|Указывает, для принудительного удаления определенного файла INF. Нельзя использовать в сочетании с **– i** параметра.|
|-i|Указывает, чтобы установить файл INF. Нельзя использовать в сочетании с **-f** параметра.|
|/?|Отображение справки в командной строке.|


## <a name="examples"></a>Примеры

-   PnPUtil.exe - a:\usbcam\USBCAM. INF добавляет файл INF, который задается параметром USBCAM. INF
-   PnPUtil.exe - c:\drivers\*INF-файл добавляет все файлы INF в c:\drivers\
-   PnPUtil.exe -i - a:\usbcam\USBCAM. Добавляет INF и установит драйвер.
-   PnPUtil.exe – e перечисляет все сторонние драйверы.
-   -d имена oem0.inf PnPUtil.exe удаляет указанный.
-   имена oem0.inf -f -d для PnPUtil.exe Принудительное удаление указанного файла INF.

## <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)

[popd](popd.md)