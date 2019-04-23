---
title: label
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bbae8bdd-97d4-4566-9118-7c95aa07645f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6dea364b1afe385d03b0519538ff7bbd6bb9df28
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59883255"
---
# <a name="label"></a>label



Создает, изменяет или удаляет метку тома (то есть имя) диска. При использовании без параметров, **метка** команда изменяет метку тома, или удаляет существующую метку.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
label [/mp] [<Volume>] [<Label>]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/MP|Указывает, что том должен рассматриваться как имени подключения точки или тома.|
|\<Тома >|Указывает букву диска (двоеточие), точку подключения или имя тома. Если указано имя тома, **/mp** параметр необязателен.|
|\<Метка >|Указывает метку для тома.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

-   Windows отображает метку тома и серийный номер (если таковой имеется) как часть списка каталогов.
-   Метка тома NTFS может быть до 32 символов, включая пробелы. Метки томов NTFS сохраняют и отобразить случай, который использовался при создании метки.
-   Если не указать значение для **метка** параметра **метка** команда отображает выходные данные в следующем формате:  
    ```
    Volume in drive C: xxxxxxxxxxx 
    Volume Serial Number is xxxx-xxxx 
    Volume label (32 characters, ENTER for none)?
    ```  
    Можно ввести новую метку тома, или нажмите клавишу ВВОД, чтобы сохранить текущую метку. При нажатии клавиши ВВОД и тома в настоящее время имеет метку, **метка** команда запрашивает со следующим сообщением:  
    ```
    Delete current volume label (Y/N)?
    ```  
    Нажмите клавишу Y, чтобы удалить метку, или нажмите клавишу N, чтобы сохранить метки.

## <a name="BKMK_examples"></a>Примеры

Чтобы пометить диск в дисководе A, который содержит сведения о продажах за июль, введите следующую команду:
```
label a:sales-july
```
Чтобы удалить метку для диска C, выполните следующие действия:
1.  В командной строке введите:  
    ```
    Label
    ```  
    Отображать результат, аналогичный приведенному ниже:  
    ```
    Volume in drive C: is Main Disk
    Volume Serial Number is 6789-ABCD
    Volume label (32 characters, ENTER for none)?
    ```  
2.  Нажмите клавишу ВВОД. Может появиться следующее сообщение:  
    ```
    Delete current volume label (Y/N)?
    ```  
3.  Нажмите клавишу Y, чтобы удалить метку.

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)