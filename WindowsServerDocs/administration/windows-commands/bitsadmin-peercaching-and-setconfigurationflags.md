---
title: bitsadmin peercaching и getconfigurationflags
description: Справочный раздел для команды битсадмин и сетконфигуратионфлагс, которая задает флаги конфигурации, определяющие, может ли компьютер передавать содержимое одноранговым узлам, а также может ли он скачивать содержимое с одноранговых узлов.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ff0a2b49-66e3-4d40-824c-6a3816055d2e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3c3ce69ce7a372311ce0c30e9b3a391ea33f45ce
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717239"
---
# <a name="bitsadmin-peercaching-and-setconfigurationflags"></a>bitsadmin peercaching и getconfigurationflags

Задает флаги конфигурации, которые определяют, может ли компьютер передавать содержимое одноранговым узлам, а также может ли он скачивать содержимое с одноранговых узлов.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /peercaching /setconfigurationflags <job> <value>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задание | Отображаемое имя задания или идентификатор GUID. |
| значение | Целое число без знака со следующей интерпретацией битов в двоичном представлении:<ul><li>Чтобы разрешить загрузку данных задания с однорангового узла, установите наименьший значащий бит.</li><li>Чтобы разрешить передачу данных задания одноранговым узлам, установите второй бит справа.</li></ul>|

## <a name="examples"></a>Примеры

Чтобы указать данные задания, которые будут скачаны с узлов для задания с именем *мидовнлоаджоб*:

```
bitsadmin /peercaching /setconfigurationflags myDownloadJob 1
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)

- [Команда кэширования битсадмин](bitsadmin-peercaching.md)
