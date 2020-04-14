---
title: Compact VDISK
description: Команды Windows форкомпакт vdisk, которые уменьшают физический размер динамически расширяющегося файла виртуального жесткого диска (VHD).
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 40ca0820-67de-4160-b62a-e9bf63fe2790
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9691be21c188fbc2c3b2e782acde127270decf56
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80847427"
---
# <a name="compact-vdisk"></a>Compact VDISK

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Уменьшает физический размер динамически расширяемого файла виртуального жесткого диска (VHD). Этот параметр полезен, так как при добавлении файлов динамически расширяемые виртуальные жесткие диски увеличиваются в размере, но при удалении файлов автоматическое уменьшение размера не уменьшается.

> [!NOTE]
> Эта команда применима только к Windows 7 и Windows Server 2008 R2.

## <a name="syntax"></a>Синтаксис
```
compact vdisk
```

## <a name="remarks"></a>Примечания

- Для выполнения этой операции необходимо выбрать динамически расширяемый виртуальный жесткий диск. Используйте команду **SELECT VDISK** , чтобы выбрать виртуальный жесткий диск и переместить фокус на него.

- Можно сжимать только динамически расширяемые виртуальные жесткие диски, которые отсоединяются или присоединяются как доступные только для чтения.

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров
Чтобы сжать динамически расширяемый виртуальный жесткий диск, введите:
```
compact vdisk
```

## <a name="additional-references"></a>Дополнительные материалы
- - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
- [подключить виртуальный диск](attach-vdisk.md)
- [подробные сведения VDISK](detail-vdisk.md)
- [Отсоединить виртуальный диск](detach-vdisk.md)
- [развернуть виртуальный диск](expand-vdisk.md)
- [Слияние VDISK](merge-vdisk.md)
- [выбрать виртуальный диск](select-vdisk.md)
- [list_1](list_1.md)
