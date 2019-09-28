---
title: UniqueID
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 64235a4a-b91c-46da-b9b0-68ee90571c2a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 64f097766daa4c87ec84f42dd53f49792a160bb9
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71363911"
---
# <a name="uniqueid"></a>UniqueID



Отображает или задает идентификатор таблицы разделов GUID (GPT) или подпись основной загрузочной записи (MBR) для диска, на котором находится фокус.

> [!IMPORTANT]
> Эта команда DiskPart недоступна ни в одном из выпусков Windows Vista.

## <a name="syntax"></a>Синтаксис

```
uniqueid disk [id={<dword> | <GUID>}] [noerr]
```

## <a name="parameters"></a>Параметры

|  Параметр   |                                                                                             Описание                                                                                              |
|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ID = {\<dword > |                                                                                               <GUID>}                                                                                                |
|    Noerr     | только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки. |

## <a name="remarks"></a>Примечания

-   Эта команда работает на базовых и динамических дисках.
-   Для завершения этой команды необходимо выбрать диск. Используйте команду **Выбор диска** , чтобы выбрать диск и переместить фокус на него.

## <a name="BKMK_examples"></a>Примеров

Чтобы отобразить подпись диска MBR с фокусом, введите:
```
uniqueid disk
```
Чтобы задать подпись диска MBR с фокусом на 5f1b2c36, введите:
```
uniqueid disk id=5f1b2c36
```
Чтобы задать идентификатор диска GPT с фокусом на baf784e7-6bbd-4cfb-aaac-e86c96e166ee, введите:
```
uniqueid disk id=baf784e7-6bbd-4cfb-aaac-e86c96e166ee
```

#### <a name="additional-references"></a>Дополнительная справка

