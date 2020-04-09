---
title: Целевой объект BdeHdCfg
description: Раздел команд Windows для **целевого объекта BdeHdCfg**, который готовит раздел для использования в качестве системного диска с помощью BitLocker и восстановления Windows.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f761d25d-8349-4ac7-ac46-6bb340a4348f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d0f3e90fbb8725360cf8db335e79721e2328ab3a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851017"
---
# <a name="bdehdcfg-target"></a>BdeHdCfg: целевой объект

Подготавливает раздел для использования в качестве системного диска с помощью BitLocker и восстановления Windows. По умолчанию эта секция создается без буквы диска.

Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
bdehdcfg -target {default|unallocated|<DriveLetter> shrink|<DriveLetter> merge}
```

#### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| default | Указывает, что программа командной строки будет следовать тому же процессу, что и мастер установки BitLocker. |
| нераспределенного | Создает системный раздел из нераспределенного пространства, доступного на диске. |
| Сжатие `<DriveLetter>` | Сокращает диск, указанный объемом, необходимым для создания активного системного раздела. Чтобы использовать эту команду, на указанном диске должно быть не менее 5% свободного места. |
| Слияние `<DriveLetter>` | Использует диск, указанный в качестве активного системного раздела. Диск операционной системы не может быть целевым объектом для слияния. |

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров

В следующем примере показано использование команды **Target** для обозначения существующего диска (P) в качестве системного диска.

```
bdehdcfg -target P: merge
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [BdeHdCfg](bdehdcfg.md)