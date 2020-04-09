---
title: битсадмин util и репаирсервице
description: Команды Windows для битсадмин util и репаирсервице, которая устраняет известные проблемы в различных версиях службы BITS.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2ac7baeb-4340-4186-bfcb-66478195378d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: aaaa6edab22031dc53d266984bb669634e3bb362
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848897"
---
# <a name="bitsadmin-util-and-repairservice"></a>битсадмин util и репаирсервице

Если не удается запустить службу BITS, используйте этот параметр для устранения известных проблем в различных версиях BITS.

**Битсадмин 1,5 и более ранних версий:**  не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /Util /RepairService [/Force]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Force|Необязательно — удаляет и повторно создает службу.|

## <a name="remarks"></a>Примечания

Этот параметр разрешает ошибки, связанные с неправильной конфигурацией службы и зависимостями в службах Windows (например, LANManworkstation) и в сетевом каталоге. Этот параметр создает выходные данные, которые указывают, разрешены ли проблемы.

> [!NOTE]
> Если служба BITS повторно создает службу, в локализованной системе в качестве строки описания службы может быть задан английский язык.

> [!IMPORTANT]
> Эта команда не поддерживается в Windows Vista.

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере восстанавливается конфигурация службы BITS.
```
C:\>bitsadmin /Util /RepairService
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)