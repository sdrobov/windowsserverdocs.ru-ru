---
title: добавление
description: Раздел Windows команды для **add_1** — добавляет в набор томов, которые должны быть теневые копии тома или добавляет псевдонимы среды псевдоним.
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 549c8560774f004a60926ce568c850fd1b71c7f9
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59889955"
---
# <a name="add"></a>добавление


Добавляет тома в набор томов, которые подлежат теневому копированию или псевдонимы в среду псевдоним. При использовании без подкоманды, **добавить** список текущих томов и псевдонимы.

> [!NOTE]
> Псевдонимы не добавляются в среду псевдоним, до создания теневой копии. Псевдонимы, немедленно добавляются с помощью **добавить псевдоним**.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
add 
add volume <Volume> [provider <ProviderID>] 
add alias <AliasName> <AliasValue>
```

## <a name="add-subcommands"></a>Добавление подкоманды

|Подкоманда|Описание|
|----------|-----------|
|том|Добавляет том к теневого копирования набора, который представляет собой набор томов в теневую копию. См. в разделе [добавить том](add-volume.md) для синтаксиса и параметров.|
|alias|Добавляет в среду псевдоним заданными именем и значением. См. в разделе [добавьте псевдоним](add-alias.md) для синтаксиса и параметров.|
|/?|Отображает справку командной строки.|

## <a name="BKMK_examples"></a>Примеры

Чтобы отобразить тома, добавляемые и псевдонимы, используемые в данный момент в среде, введите:
```
add
```
В следующем примере вывод, что диск C был добавлен в набор теневого копирования:
```
Volume c: alias System1    GUID \\?\Volume{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}\
1 volume in Shadow Copy Set.
No Diskshadow aliases in the environment.
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)