---
title: popd
description: Узнайте, как изменить каталог на каталог, сохраненный в команде pushd.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 8a9e0a301a5f8b46e1907a4f43c5ed9247b85f77
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71372226"
---
# <a name="popd"></a>popd

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет текущий каталог на каталог, который был последним сохранен командой **pushd** .
Примеры использования этой команды см. в разделе [примеры](#BKMK_examples).

## <a name="syntax"></a>Синтаксис
```
popd
```

### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания
-   Каждый раз, когда вы используете команду **pushd** , хранится один каталог для использования. Однако можно хранить несколько каталогов с помощью команды **pushd** многократно.
    Каталоги последовательно хранятся в виртуальном стеке. Если команда **pushd** используется один раз, то каталог, в котором используется команда, помещается в нижнюю часть стека. При повторном использовании команды второй каталог помещается поверх первого. Процесс повторяется каждый раз при использовании команды **pushd** .
    Вы можете использовать команду **popd** , чтобы изменить текущий каталог на каталог, сохраненный с помощью команды **pushd** . При использовании команды **popd** каталог в верхней части стека удаляется из стека, а текущий каталог изменяется на этот каталог. При повторном использовании команды **popd** происходит удаление следующего каталога в стеке.
-   Если расширения команд включены, команда **popd** удаляет все назначения букв дисков, созданные с помощью **pushd**.

## <a name="BKMK_examples"></a>Примеров
В следующем примере показано, как можно использовать команду **pushd** и команду **popd** в пакетной программе для изменения текущего каталога, в котором выполнялась программа пакетной службы, а затем изменить ее обратно:

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
-   [pushd](pushd.md)
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

