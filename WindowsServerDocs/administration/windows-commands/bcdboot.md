---
title: bcdboot
description: Раздел команд Windows для **BCDboot**, который быстро настраивает системный раздел или восстанавливает среду загрузки, расположенную в системном разделе.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e62a250e-08e9-47f6-89d1-e6002560ab57
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 637170cbd8ee4f3c11ee1dc77a0cd49b5dfa3038
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851087"
---
# <a name="bcdboot"></a>bcdboot

Позволяет быстро настроить системный раздел или восстановить среду загрузки, расположенную в системном разделе. Системный раздел настраивается путем копирования простого набора файлов данные конфигурации загрузки (BCD) в существующий пустой раздел.

## <a name="syntax"></a>Синтаксис

```
bcdboot <source> [/l] [/s]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| источник | Указывает расположение каталога Windows, используемого в качестве источника для копирования файлов среды загрузки. |
| /l | Задает языковой стандарт. Язык по умолчанию — английский (США). |
| /s | Указывает букву тома системного раздела. По умолчанию используется системный раздел, определяемый встроенным по. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Сведения о том, где найти BCDboot и примеры использования этой команды, см. в разделе [Параметры командной строки BCDboot](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-8.1-and-8/hh824874(v=win.10)x) .

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)