---
title: add
description: Команды Windows для **добавления**, которая добавляет тома в набор томов, предназначенных для теневого копирования, или добавляет псевдонимы в среду псевдонима.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 47efce7a-86d2-4872-ae31-baa108757afd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9895082cc10223fd08cff6916c20c3af5613e947
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851347"
---
# <a name="add"></a>add

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

| Подкоманда | Описание |
| ---------- | ----------- |
| том | Добавляет том в набор теневых копий, который представляет собой набор томов, предназначенных для теневого копирования. См. раздел [Добавление тома](add-volume.md) для синтаксиса и параметров. |
| псевдоним | Добавляет заданное имя и значение в среду псевдонима. Синтаксис и параметры см. в разделе [Добавление псевдонима](add-alias.md) . |
| `/?` | Отображает справку в командной строке. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

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

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)