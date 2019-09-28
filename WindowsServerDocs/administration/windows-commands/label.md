---
title: label
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: e66a2d9a7d28462b287084e3f8b129ffc03800bd
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71374788"
---
# <a name="label"></a>label



Создает, изменяет или удаляет метку тома (то есть имя) диска. Если используется без параметров, команда **Label** изменяет метку текущего тома или удаляет существующую метку.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
label [/mp] [<Volume>] [<Label>]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/MP|Указывает, что том следует рассматривать как точку подключения или имя тома.|
|@no__t 0Volume >|Указывает букву диска (за которой следует двоеточие), точку подключения или имя тома. Если указано имя тома, параметр **/MP** не требуется.|
|@no__t 0Label >|Указывает метку для тома.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

- Windows отображает метку тома и серийный номер (если они есть) в составе списка каталогов.
- Длина метки тома NTFS может составлять до 32 символов, включая пробелы. Метки томов NTFS содержат и отображают вариант, который использовался при создании метки.
- Если не указать значение для параметра **метки** , команда **Метка** будет отображать выходные данные в следующем формате:  
  ```
  Volume in drive C: xxxxxxxxxxx 
  Volume Serial Number is xxxx-xxxx 
  Volume label (32 characters, ENTER for none)?
  ```  
  Можно ввести новую метку тома или нажать клавишу ВВОД для сохранения текущей метки. Если нажать клавишу ВВОД и в настоящий момент в томе есть метка, команда **Label** выдаст следующее сообщение:  
  ```
  Delete current volume label (Y/N)?
  ```  
  Нажмите клавишу Y, чтобы удалить метку, или клавишу N для сохранения метки.

## <a name="BKMK_examples"></a>Примеров

Чтобы пометить диск в дисководе A, который содержит сведения о продажах за Июль, введите:
```
label a:sales-july
```
Чтобы удалить текущую метку для диска C, выполните следующие действия.
1. В командной строке введите:  
   ```
   Label
   ```  
   Должны отобразиться выходные данные, аналогичные приведенным ниже.  
   ```
   Volume in drive C: is Main Disk
   Volume Serial Number is 6789-ABCD
   Volume label (32 characters, ENTER for none)?
   ```  
2. Нажмите клавишу ВВОД. Должен отобразиться следующий запрос:  
   ```
   Delete current volume label (Y/N)?
   ```  
3. Нажмите клавишу Y, чтобы удалить текущую метку.

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)