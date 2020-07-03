---
title: bitsadmin getminretrydelay
description: Справочная статья по команде битсадмин жетминретриделай, которая получает время ожидания (в секундах), в течение которого служба будет ожидать временной ошибки, прежде чем пытаться переместить файл.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 54f0abab-c129-40ed-a603-50f464d26011
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 066eb9a2c967d9d5e92aa8dbad2001a65a682796
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927017"
---
# <a name="bitsadmin-getminretrydelay"></a>bitsadmin getminretrydelay

Возвращает продолжительность времени в секундах, в течение которого служба будет ожидать после возникновения временной ошибки, прежде чем пытаться переместить файл.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getminretrydelay <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a>Примеры

Для получения минимальной задержки повтора для задания с именем *мидовнлоаджоб*:

```
bitsadmin /getminretrydelay myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
