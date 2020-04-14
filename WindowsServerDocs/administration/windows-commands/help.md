---
title: help
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c65b5ac3-711a-4368-95b8-ba82e2d00713
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f7b6f3a563c59a55ff92b38f0854437b96478f6c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80842347"
---
# <a name="help"></a>help



Предоставляет оперативную информацию о системных командах (то есть командах, отличных от сетевых). Если используется без параметров, **Справочные** списки и краткое описание каждой системной команды.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
help [<Command>] 
[<Command>] /?
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Команда \<>|Указывает имя команды, сведения о которой требуется получить.|

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы просмотреть сведения о команде **Robocopy** , введите одно из следующих действий:
```
help robocopy
robocopy /? 
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)