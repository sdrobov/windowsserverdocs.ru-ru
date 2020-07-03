---
title: битсадмин жетпроксилист — извлекает список прокси-серверов для указанного задания.
description: Справочная статья по команде битсадмин жетпроксилист, которая получает список прокси-серверов для указанного задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: eebfa727-d8f1-4ae3-9382-6d8ffe8c3df3
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 60c66db909b9b62d33ffda09e3b696362b6a65a0
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926819"
---
# <a name="bitsadmin-getproxylist"></a>bitsadmin getproxylist

Извлекает разделенный запятыми список прокси-серверов, используемых для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getproxylist <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a>Примеры

Чтобы получить список прокси-серверов для задания с именем *мидовнлоаджоб*:

```
bitsadmin /getproxylist myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
