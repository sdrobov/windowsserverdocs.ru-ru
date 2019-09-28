---
title: Восстановление реестра
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a51f1c0c-969b-4b76-930a-c8bb14dea26e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d6c121256cecaebc26e2c402d9b9ced8890eddc2
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71384674"
---
# <a name="reg-restore"></a>Восстановление реестра



Записывает сохраненные разделы и записи обратно в реестр.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
Reg restore <KeyName> <FileName>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|@no__t 0KeyName >|Указывает полный путь к восстанавливаемому подразделу. Операция восстановления работает только с локальным компьютером. KeyName должен содержать допустимый корневой ключ. Допустимые корневые ключи: HKLM, HKCU, HKCR, HKU и ХККК.|
|\<Имя файла >|Указывает имя и путь к файлу, содержимое которого записывается в реестр. Этот файл должен быть создан заранее с операцией **reg save** с помощью расширения. ВИЧ.|
|/?|Отображает справку по **восстановлению реестра** в командной строке.|

## <a name="remarks"></a>Примечания

-   Перед тем как вносить изменения в записи реестра, сохраните родительский подраздел с операцией **reg save** . Если операция изменения не удалась, восстановите исходный подраздел с операцией **восстановления reg** .
-   В следующей таблице перечислены возвращаемые значения для операции **reg restore** .

|Значение|Описание|
|-----|-----------|
|0|Success|
|1|Отказ|

## <a name="BKMK_examples"></a>Примеров

Чтобы восстановить файл с именем Нтркбкуп. ВИЧ в ключ Хклм\софтваре\микрософт\рескит и перезаписать существующее содержимое ключа, введите:
```
REG RESTORE HKLM\Software\Microsoft\ResKit NTRKBkUp.hiv
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)