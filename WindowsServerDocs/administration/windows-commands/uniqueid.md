---
title: Уникальный идентификатор
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: d237f4d6d3562e3787efe28ca98f9dc553d74898
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66440750"
---
# <a name="uniqueid"></a>Уникальный идентификатор



Отображает или задает идентификатор GUID подпись таблицы разделов (GPT) идентификатор или master boot запись (MBR) для диска с фокусом.

> [!IMPORTANT]
> Эта команда DiskPart не доступна в любом выпуске Windows Vista.

## <a name="syntax"></a>Синтаксис

```
uniqueid disk [id={<dword> | <GUID>}] [noerr]
```

## <a name="parameters"></a>Параметры

|  Параметр   |                                                                                             Описание                                                                                              |
|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id={\<dword> |                                                                                               <GUID>}                                                                                                |
|    успешного     | для использования в сценариях. При обнаружении ошибки, DiskPart продолжает обрабатывать команды, как если бы ошибки не было. Без этого параметра по ошибке будет возобновлено DiskPart завершить работу с кодом ошибки. |

## <a name="remarks"></a>Примечания

-   Эта команда работает в базовых и динамических дисков.
-   Для успешного выполнения этой команды необходимо выбрать диск. Используйте **выберите диск** команду, чтобы выбрать диск и перетянуть внимание к нему.

## <a name="BKMK_examples"></a>Примеры

Чтобы отобразить сигнатуру MBR-диске с фокусом, введите следующую команду:
```
uniqueid disk
```
Чтобы задать подпись диска MBR с фокусом 5f1b2c36, введите следующую команду:
```
uniqueid disk id=5f1b2c36
```
Чтобы задать идентификатор диска GPT с фокусом baf784e7-6bbd-4cfb-aaac-e86c96e166ee, введите следующую команду:
```
uniqueid disk id=baf784e7-6bbd-4cfb-aaac-e86c96e166ee
```

#### <a name="additional-references"></a>Дополнительная справка

