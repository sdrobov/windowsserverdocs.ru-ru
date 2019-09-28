---
title: pnputil
description: Узнайте, как управлять хранилищем драйверов с помощью служебной программы pnputil. exe.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: f20c60bfd9ae33497dd356c7797b9fb1d2b51d18
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71372290"
---
# <a name="pnputil"></a>pnputil

Средство PnPUtil. exe — это служебная программа командной строки, которую можно использовать для управления хранилищем драйверов. Средство PnPUtil можно использовать для добавления пакетов драйверов, удаления пакетов драйверов и вывода списка пакетов драйверов, которые находятся в хранилище.

## <a name="syntax"></a>Синтаксис

```
pnputil.exe [-f | -i] [ -? | -a | -d | -e ] <INF name>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|-a|Указывает, что добавляет определенный INF-файл.|
|-d|Указывает, следует удалить указанный INF-файл.|
|-e|Задает перечисление всех сторонних INF-файлов.|
|-f|Указывает принудительное удаление идентифицированного INF-файла. Нельзя использовать в сочетании с параметром **– i** .|
|-i|Задает установку идентифицированного INF-файла. Нельзя использовать в сочетании с параметром **-f** .|
|/?|Отображение справки в командной строке.|


## <a name="examples"></a>Примеры

-   PnPUtil. exe-a А:\усбкам\усбкам. INF добавляет INF-файл, указанный параметром УСБКАМ. ФАЙЛУ
-   PnPUtil. exe-a c:\ drivers\*.inf добавляет все INF-файлы в к:\дриверс\
-   PnPUtil. exe-i-a А:\усбкам\усбкам. INF добавляет и устанавливает указанный драйвер.
-   средство PnPUtil. exe – e перечисляет драйверы сторонних производителей.
-   средство PnPUtil. exe-d oem0. INF удаляет указанный объект.
-   средство PnPUtil. exe-f-d oem0. INF вызывает принудительное удаление указанного INF-файла.

## <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

[Командой](popd.md)