---
title: list
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 57b6c8d0-872e-4dba-9715-1db8ab892e98
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d60c42b868a1e9a26e3168e4b489573f9f87e179
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841107"
---
# <a name="list"></a>list



Перечисляет модули записи, теневые копии или зарегистрированные в настоящее время поставщики теневого копирования, которые находятся в системе. Если используется без параметров, **список** отображает справку в командной строке.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
list writers [metadata | detailed | status]
list shadows {all | set <SetID> | id <ShadowID>}
list providers
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|средствами|Выводит список модулей записи. Синтаксис и параметры см. в разделе [модули записи списка](list-writers.md) .|
|темно|Список постоянных и существующих непостоянных теневых копий. Синтаксис и параметры см. в разделе [список теней](list-shadows.md) .|
|поставщики|Перечисляет зарегистрированные в настоящее время поставщики теневого копирования. Синтаксис и параметры см. в разделе [поставщики списков](list-providers.md) .|

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы получить список всех теневых копий, введите:
```
list shadows all
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)