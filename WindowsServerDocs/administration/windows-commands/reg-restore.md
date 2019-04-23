---
title: Восстановление REG
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 0025a37ed8ca50b47e7750501a7362659b500537
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59858775"
---
# <a name="reg-restore"></a>Восстановление REG



Записывает сохраненные вложенные разделы и записи обратно в реестр.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
Reg restore <KeyName> <FileName>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<KeyName>|Указывает полный путь к разделу для восстановления. Операция восстановления работает только с локального компьютера. KeyName должен содержать допустимый корневой раздел. Действительный корневой ключи являются: HKLM, HKCU, HKCR, HKU и HKCC.|
|\<Имя файла >|Указывает имя и путь к файлу с содержимым, который будет записан в реестре. Этот файл должен быть создан заранее с **сохранить reg** операции, используя расширение .hiv.|
|/?|Отображает справку по **восстановления reg** в командной строке.|

## <a name="remarks"></a>Примечания

-   Прежде чем изменять записи в реестре, родительский раздел с необходимо сохранить **сохранить reg** операции. Раздел с можно восстановить в случае сбоя редактирования **восстановления reg** операции.
-   В следующей таблице перечислены возвращаемые значения для **восстановления reg** операции.

|Значение|Описание|
|-----|-----------|
|0|Success|
|1|Отказ|

## <a name="BKMK_examples"></a>Примеры

Чтобы восстановить файл с именем NTRKBkUp.hiv в ключ HKLM\Software\Microsoft\ResKit и перезаписать существующее содержимое ключа, введите следующую команду:
```
REG RESTORE HKLM\Software\Microsoft\ResKit NTRKBkUp.hiv
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)