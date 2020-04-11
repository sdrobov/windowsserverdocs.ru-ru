---
title: битсадмин сетпиркачингфлагс
description: Раздел команд Windows для **битсадмин сетпиркачингфлагс**, который устанавливает флаги, определяющие, могут ли файлы задания кэшироваться и обслуживаться одноранговым узлам, а также может ли задание скачивать содержимое с одноранговых узлов.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3f54a127-fb68-49a5-b843-664ec833df67
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1b4a7807975fb46440301e30b1fdbd01784d7c85
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81122778"
---
# <a name="bitsadmin-setpeercachingflags"></a>битсадмин сетпиркачингфлагс

Устанавливает флаги, определяющие, могут ли файлы задания кэшироваться и обслуживаться одноранговым узлам, а также может ли задание скачивать содержимое с одноранговых узлов.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /setpeercachingflags <job> <value>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| задания | Отображаемое имя задания или идентификатор GUID. |
| value | Целое число без знака, включая:<ul><li>**1.** задание может скачивать содержимое с одноранговых узлов.</li><li>**2.** файлы задания могут кэшироваться и обслуживаться одноранговыми узлами.</li></ul> |

## <a name="examples"></a>Примеры

В следующем примере устанавливаются флаги для задания с именем *мидовнлоаджоб*, что позволяет ему скачивать содержимое с одноранговых узлов.

```
C:\>bitsadmin /setpeercachingflags myDownloadJob 1
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)