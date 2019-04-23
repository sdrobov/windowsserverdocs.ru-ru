---
title: popd
description: Узнайте, как изменить каталог на каталог, наиболее недавно командой pushd.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8a4c52d5-9fd1-4eac-9c0c-5767b25728ed
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: 6da6dc9d1fc2d8965f8a081831cb1150375209a4
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59827465"
---
# <a name="popd"></a>popd

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет текущий каталог на каталог, который недавно был сохранен программой **pushd** команды.
Примеры для использования этой команды, см. в разделе [примеры](#BKMK_examples).

## <a name="syntax"></a>Синтаксис
```
popd
```

### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания
-   Каждый раз при использовании **pushd** команды одного каталога хранится для использования. Тем не менее, можно сохранить несколько каталогов с помощью **pushd** команды несколько раз.
    Каталоги сохраняются последовательно в виртуальный стек. Если вы используете **pushd** команды один раз, каталог, в котором используется команда помещается в нижней части стека. Если вы используете команду второй каталог помещается над первым. Процесс повторяется каждый раз при использовании **pushd** команды.
    Можно использовать **popd** команду, чтобы сменить текущий каталог в каталог, сохраненный с последним **pushd** команды. Если вы используете **popd** команда каталог в стеке удаляется из стека и текущий каталог был изменен в этот каталог. Если вы используете **popd** команду еще раз, будет удален следующий каталог в стеке.
-   Если включены расширения команд, **popd** команда удаляет все имена дисков, назначенные созданные **pushd**.

## <a name="BKMK_examples"></a>Примеры
В следующем примере показано, как можно использовать **pushd** команды и **popd** команды в пакетном файле, чтобы сменить текущий каталог от того, в котором она была запущена и затем изменить его обратно:

```
@echo off
rem This batch file deletes all .txt files in a specified directory
pushd %1
del *.txt
popd
cls
echo All text files deleted in the %1 directory
```

## <a name="additional-references"></a>Дополнительные ссылки
-   [PUSHD](pushd.md)
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)

