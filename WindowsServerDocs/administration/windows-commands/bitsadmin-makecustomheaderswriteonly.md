---
title: битсадмин макекустомхеадерсвритеонли
description: Раздел команд Windows для **битсадмин макекустомхеадерсвритеонли**, который делает НАСТРАИВАЕМЫЕ заголовки HTTP задания только для записи.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 9183b1b5de51020c5c6d2efad2c0a788d158a183
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850247"
---
# <a name="bitsadmin-makecustomheaderswriteonly"></a>битсадмин макекустомхеадерсвритеонли

Сделайте пользовательские HTTP-заголовки задания только для записи.

> [!Important]
> Это действие нельзя отменить.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /makecustomheaderswriteonly <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задания | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере пользовательские заголовки HTTP записываются только для записи для задания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /makecustomheaderswriteonly myDownloadJob
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)