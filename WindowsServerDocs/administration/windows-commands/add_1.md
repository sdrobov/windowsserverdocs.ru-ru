---
title: добавление
description: Раздел команд Windows для **Add_1** . добавляет тома в набор томов, которые должны быть теневыми копиями, или добавляет псевдонимы в среду псевдонима.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 47efce7a-86d2-4872-ae31-baa108757afd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d1aaa211938d14a0019d29e64867f4df2475a877
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71382781"
---
# <a name="add"></a>добавление


Добавляет тома в набор томов, которые должны быть теневыми копиями, или добавляет псевдонимы в среду псевдонима. Если используется без подкоманд, **добавьте** список текущих томов и псевдонимов.

> [!NOTE]
> Псевдонимы не добавляются в среду псевдонима до тех пор, пока не будет создана теневая копия. Псевдонимы, которые необходимо выполнить немедленно, следует добавлять с помощью команды **Добавить псевдоним**.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
add 
add volume <Volume> [provider <ProviderID>] 
add alias <AliasName> <AliasValue>
```

## <a name="add-subcommands"></a>Добавить подкоманды

|Подкоманда|Описание|
|----------|-----------|
|том|Добавляет том в набор теневых копий, который представляет собой набор томов, предназначенных для теневого копирования. См. раздел [Добавление тома](add-volume.md) для синтаксиса и параметров.|
|alias|Добавляет заданное имя и значение в среду псевдонима. Синтаксис и параметры см. в разделе [Добавление псевдонима](add-alias.md) .|
|/?|Отображает справку в командной строке.|

## <a name="BKMK_examples"></a>Примеров

Чтобы отобразить добавленные тома и псевдонимы, которые в настоящее время находятся в среде, введите:
```
add
```
Следующие выходные данные показывают, что диск C добавлен в набор теневых копий:
```
Volume c: alias System1    GUID \\?\Volume{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}\
1 volume in Shadow Copy Set.
No Diskshadow aliases in the environment.
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)