---
title: bitsadmin setaclflag
description: Раздел команд Windows для **битсадмин сетаклфлаг**, который задает флаги распространения списка управления доступом (ACL).
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6e3bcda0-827d-4dfd-8384-d1da018f3e10
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f0aae550e94d04db518edccafb1d6bcf46d0320b
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81123067"
---
# <a name="bitsadmin-setaclflag"></a>bitsadmin setaclflag

Задает флаги распространения списка управления доступом (ACL) для задания. Флаги указывают, что вы хотите сохранить сведения о владельце и списке ACL с загружаемым файлом. Например, чтобы сохранить владельца и группу с файлом, задайте для параметра **flags** значение `og`.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /setaclflag <job> <flags>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| задания | Отображаемое имя задания или идентификатор GUID. |
| flags | Укажите одно или несколько значений, включая:<ul><li>**o** — копирование сведений о владельце с помощью файла.</li><li>**g** — копирование сведений о группе с помощью файла.</li><li>**d** — копирование сведений о избирательном списке управления доступом (DACL) с помощью файла.</li><li>**s** -копирование данных системного списка управления доступом (SACL) с помощью файла.</li></ul> |

## <a name="remarks"></a>Примечания

Параметр/сетаклфлаг используется для сохранения сведений о владельце и списке управления доступом, когда задание скачивает данные из общего ресурса Windows (SMB).

## <a name="examples"></a>Примеры

В следующем примере задается флаги распространения списка управления доступом для задания с именем *мидовнлоаджоб* , чтобы сохранить сведения о владельце и группе с скачанными файлами.

```
C:\>bitsadmin /setaclflags myDownloadJob og
```

## <a name="additional-references"></a>Дополнительные материалы

[Ключ синтаксиса командной строки](command-line-syntax-key.md)&reg;"    