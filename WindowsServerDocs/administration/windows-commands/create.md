---
title: create
description: Справочный раздел по команде CREATE, который создает раздел или теневую секцию на диске, том на одном или нескольких дисках или виртуальный жесткий диск (VHD).
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b45acde1-8f4f-4ec3-b905-d8188f884af8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f371bee591e29a45b1488b2c36112b55ed54d3f8
ms.sourcegitcommit: fad2ba64bbc13763772e21ed3eabd010f6a5da34
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2020
ms.locfileid: "82993194"
---
# <a name="create"></a>create

Создает раздел или тень на диске, том на одном или нескольких дисках или виртуальный жесткий диск (VHD). Если вы используете эту команду для создания тома на теневом диске, в наборе теневых копий уже должен быть хотя бы один том.

## <a name="syntax"></a>Синтаксис

```
create partition
create volume
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| [создать основную команду Секции](create-partition-primary.md) | Создает основной раздел на базовом диске с фокусом. |
| [Команда "создать секцию EFI"](create-partition-efi.md) | Создает системный раздел интерфейса EFI на диске с таблицей разделов GPT на компьютерах на базе процессоров Itanium. |
| [Создание расширенной команды Partition](create-partition-extended.md) | Создает дополнительный раздел на диске с фокусом. |
| [Создание логической команды секции](create-partition-logical.md) | Создает логическую секцию в существующем расширенном разделе. |
| [Команда создания секции MSR](create-partition-msr.md) | Создает MSR-раздел на диске с таблицей разделов GUID (GPT). |
| [Команда создания простого тома](create-volume-simple.md) | Создает простой том на указанном динамическом диске. |
| [Команда создания зеркального отображения тома](create-volume-mirror.md) | Создает зеркало тома с использованием двух указанных динамических дисков. |
| [Команда создания тома RAID](create-volume-raid.md) | Создает том RAID-5, используя три или более указанных динамических диска. |
| [Команда создания чередующихся томов](create-volume-stripe.md) | Создает чередующийся том с использованием двух или более указанных динамических дисков. |

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
