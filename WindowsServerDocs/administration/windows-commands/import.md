---
title: импорт
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7bd78d76-0560-4d47-944c-fe960be2c10b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ddef3958bc431519e3cb89b658a58d1f4dba6938
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59835265"
---
# <a name="import"></a>импорт



Импортирует переносимой теневой копии из загруженных метаданных файла в систему.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
import
```

## <a name="remarks"></a>Примечания

-   Немедленно переносимых теневых копий не хранятся в системе. Сведения о них хранятся в файле резервной копии компонентов документа XML, который DiskShadow автоматически запрашивает и сохраняет в CAB-файл метаданных в рабочем каталоге. Можно изменить путь и имя этого файла с помощью **задать метаданные** команды.
-   Перед использованием **импорта**, необходимо загрузить файл метаданных DiskShadow с помощью **загрузить метаданные** команды.

## <a name="BKMK_examples"></a>Примеры

Ниже приведен пример сценария DiskShadow, который демонстрирует использование **импорта** команды:
```
#Sample DiskShadow script demonstrating IMPORT
SET CONTEXT PERSISTENT
SET CONTEXT TRANSPORTABLE
SET METADATA transHWshadow_p.cab
#P: is the volume supported by the Hardware Shadow Copy provider
ADD VOLUME P:
CREATE
END BACKUP
#The (transportable) shadow copy is not in the system yet.
#You can reset or exit now if you wish.

LOAD METADATA transHWshadow_p.cab
IMPORT
#The shadow copy will now be loaded into the system.
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)