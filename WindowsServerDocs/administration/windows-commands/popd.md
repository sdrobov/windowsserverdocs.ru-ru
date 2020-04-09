---
title: popd
description: Узнайте, как изменить каталог на каталог, сохраненный в команде pushd.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8a4c52d5-9fd1-4eac-9c0c-5767b25728ed
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: b66b5edd2fa068923650f578d13f30631a8602ad
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80837477"
---
# <a name="popd"></a>popd

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет текущий каталог на каталог, который был последним сохранен командой **pushd** .
Примеры использования этой команды см. в разделе [примеры](#BKMK_examples).

## <a name="syntax"></a>Синтаксис
```
popd
```

#### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/?|Отображает справку в командной строке.|

## <a name="remarks"></a>Примечания
-   Каждый раз, когда вы используете команду **pushd** , хранится один каталог для использования. Однако можно хранить несколько каталогов с помощью команды **pushd** многократно.
    Каталоги последовательно хранятся в виртуальном стеке. Если команда **pushd** используется один раз, то каталог, в котором используется команда, помещается в нижнюю часть стека. При повторном использовании команды второй каталог помещается поверх первого. Процесс повторяется каждый раз при использовании команды **pushd** .
    Вы можете использовать команду **popd** , чтобы изменить текущий каталог на каталог, сохраненный с помощью команды **pushd** . При использовании команды **popd** каталог в верхней части стека удаляется из стека, а текущий каталог изменяется на этот каталог. При повторном использовании команды **popd** происходит удаление следующего каталога в стеке.
-   Если расширения команд включены, команда **popd** удаляет все назначения букв дисков, созданные с помощью **pushd**.

## <a name="examples"></a><a name="BKMK_examples"></a>Примеров
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

## <a name="additional-references"></a>Дополнительные материалы
-   [pushd](pushd.md)
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

