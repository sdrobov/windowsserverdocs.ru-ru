---
title: bitsadmin setpeercachingflags
description: Справочный раздел по команде битсадмин сетпиркачингфлагс, который устанавливает флаги, определяющие, могут ли файлы задания кэшироваться и обслуживаться одноранговым узлам, а также может ли задание скачивать содержимое с одноранговых узлов.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3f54a127-fb68-49a5-b843-664ec833df67
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8b66b169c38ac050ecaaf6546365547148faa9cf
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717269"
---
# <a name="bitsadmin-setpeercachingflags"></a>bitsadmin setpeercachingflags

Устанавливает флаги, определяющие, могут ли файлы задания кэшироваться и обслуживаться одноранговым узлам, а также может ли задание скачивать содержимое с одноранговых узлов.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /setpeercachingflags <job> <value>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| задание | Отображаемое имя задания или идентификатор GUID. |
| значение | Целое число без знака, включая:<ul><li>**1.** задание может скачивать содержимое с одноранговых узлов.</li><li>**2.** файлы задания могут кэшироваться и обслуживаться одноранговыми узлами.</li></ul> |

## <a name="examples"></a>Примеры

Чтобы разрешить заданию с именем *мидовнлоаджоб* скачивать содержимое с одноранговых узлов:

```
bitsadmin /setpeercachingflags myDownloadJob 1
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
