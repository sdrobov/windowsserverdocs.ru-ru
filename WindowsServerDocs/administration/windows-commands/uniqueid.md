---
title: UniqueID
description: Справочный раздел по UniqueId, который отображает или задает идентификатор таблицы разделов GUID (GPT) или подпись основной загрузочной записи (MBR) для диска с фокусом.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 64235a4a-b91c-46da-b9b0-68ee90571c2a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: efaafe889f04511ceef7441b0a42b73259aadedf
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721183"
---
# <a name="uniqueid"></a>UniqueID

Отображает или задает идентификатор таблицы разделов GUID (GPT) или подпись основной загрузочной записи (MBR) для диска, на котором находится фокус.

> [!IMPORTANT]
> Эта команда DiskPart недоступна ни в одном из выпусков Windows Vista.

## <a name="syntax"></a>Синтаксис

```
uniqueid disk [id={<dword> | <GUID>}] [noerr]
```

### <a name="parameters"></a>Параметры

|  Параметр   |                                                                                             Описание                                                                                              |
|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ID = {\<DWORD> |                                                                                               <GUID>}                                                                                                |
|    Noerr     | Только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки. |

## <a name="remarks"></a>Примечания

-   Эта команда работает на базовых и динамических дисках.
-   Для завершения этой команды необходимо выбрать диск. Используйте команду **Выбор диска** , чтобы выбрать диск и переместить фокус на него.

## <a name="examples"></a>Примеры

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

## <a name="additional-references"></a>Дополнительные ссылки

