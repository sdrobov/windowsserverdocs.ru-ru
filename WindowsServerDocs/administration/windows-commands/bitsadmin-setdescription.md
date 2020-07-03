---
title: bitsadmin setdescription
description: Справочная статья по команде битсадмин SetDescription, которая задает описание указанного задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1e46a5dd-4637-4a2e-b88f-d3f85b177db8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9c22909193667ff3222576010498d7b2fbcf14c7
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927831"
---
# <a name="bitsadmin-setdescription"></a>bitsadmin setdescription

Задает описание для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /setdescription <job> <description>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| задание | Отображаемое имя задания или идентификатор GUID. |
| description | Текст, используемый для описания задания. |

## <a name="examples"></a>Примеры

Чтобы получить описание задания с именем *мидовнлоаджоб*, выполните следующие действия.

```
bitsadmin /setdescription myDownloadJob music_downloads
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
