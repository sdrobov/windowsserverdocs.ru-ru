---
title: bitsadmin getaclflags
description: Раздел команд Windows для **битсадмин жетаклфлагс**, который извлекает флаги распространения списка управления доступом (ACL).
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 99266def-7479-4430-a61c-98ec433fa88b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d53018e2fa5c659c8cf4b0ec985beda848a8c1af
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850797"
---
# <a name="bitsadmin-getaclflags"></a>bitsadmin getaclflags

Извлекает флаги распространения списка управления доступом (ACL), отражающие наследование элементов дочерними объектами.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getaclflags <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| задания | Отображаемое имя задания или идентификатор GUID. |

## <a name="remarks"></a>Примечания

Отображает одно или несколько из следующих значений флагов:

- **o** — копирование сведений о владельце с помощью файла.

- **g** — копирование сведений о группе с помощью файла.

- **d** — копирование сведений о избирательном списке управления доступом (DACL) с помощью файла.

- **s** -копирование данных системного списка управления доступом (SACL) с помощью файла.

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере извлекаются флаги распространения списка управления доступом для задания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /getaclflags myDownloadJob
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)