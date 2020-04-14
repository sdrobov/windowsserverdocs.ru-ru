---
title: битсадмин
description: Раздел команд Windows для **битсадмин**, который получает приоритет указанного задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: b27829a0fb852abb88c88a65e61e8d7693ca2df2
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850547"
---
# <a name="bitsadmin-getpriority"></a>битсадмин

Возвращает приоритет указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getpriority <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задания | Отображаемое имя задания или идентификатор GUID. |

## <a name="remarks"></a>Примечания

Приоритет этой команды может быть следующим:

- **ПЕРЕДНЕГО плана**

- **ВЫСОКОМ**

- **ОБЫЧНО**

- **НИЗШУЮ**

- **Неизвестный**

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере извлекается приоритет задания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /getpriority myDownloadJob
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
