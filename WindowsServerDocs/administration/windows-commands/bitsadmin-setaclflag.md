---
title: bitsadmin setaclflag
description: Раздел команд Windows для битсадмин сетаклфлаг, который задает флаги распространения списка управления доступом.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6e3bcda0-827d-4dfd-8384-d1da018f3e10
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4ac47e554dde6a555e891d89668cd12fec3179d4
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849677"
---
# <a name="bitsadmin-setaclflag"></a>bitsadmin setaclflag

Задает флаги распространения списка управления доступом (ACL) для задания. Флаги указывают, что вы хотите сохранить сведения о владельце и списке ACL с загружаемым файлом. Например, чтобы сохранить владельца и группу с файлом, установите **флаги** в значение `OG`.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetAclFlags <Job> <Flags>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|
|Флажки|Укажите одно или несколько из следующих значений флагов:</br>-O: копирование сведений о владельце с помощью файла.</br>-G: копирование сведений о группе с помощью файла.</br>-D: копирование сведений DACL в файл.</br>-S: копирование сведений SACL с помощью файла.|

## <a name="remarks"></a>Примечания

Параметр Сетаклфлагс используется для сохранения сведений о владельце и списке управления доступом, когда задание скачивает данные из общего ресурса Windows (SMB).

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере задается флаги распространения списка управления доступом для задания с именем *мидовнлоаджоб* , чтобы сохранить сведения о владельце и группе с скачанными файлами.
```
C:\>bitsadmin /setaclflags myDownloadJob OG
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)