---
title: bcdboot
description: Справочная статья по команде BCDboot, которая быстро настраивает системный раздел или восстановление среды загрузки, расположенной в системном разделе.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e62a250e-08e9-47f6-89d1-e6002560ab57
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 84041836c90987e358a6b5624d4f9b4124994263
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86955826"
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
| source | Указывает расположение каталога Windows, используемого в качестве источника для копирования файлов среды загрузки. |
| /l | Задает языковой стандарт. Язык по умолчанию — английский (США). |
| /s | Указывает букву тома системного раздела. По умолчанию используется системный раздел, определяемый встроенным по. |

## <a name="examples"></a>Примеры

Сведения о том, где найти BCDboot и примеры использования этой команды, см. в разделе [Параметры командной строки BCDboot](/previous-versions/windows/it-pro/windows-8.1-and-8/hh824874(v=win.10)) .

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
