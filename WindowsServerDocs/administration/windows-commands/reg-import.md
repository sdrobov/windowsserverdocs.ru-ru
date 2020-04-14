---
title: импорт реестра
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0be103de-08fc-4f02-b590-361782680b3e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0816297e837bbce91ca069e3506405cbdb53c51a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80836427"
---
# <a name="reg-import"></a>импорт реестра



Копирует содержимое файла, содержащего экспортированные подразделы, записи и значения реестра, в реестр локального компьютера.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
Reg import FileName
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<имя файла >|Указывает имя и путь к файлу, который содержит содержимое, копируемое в реестр локального компьютера. Этот файл должен быть создан заранее с помощью команды **reg export**.|
|/?|Отображает справку по **импорту реестра** в командной строке.|

## <a name="remarks"></a>Примечания

В следующей таблице перечислены возвращаемые значения для операции **reg import** .

|Значение|Описание|
|-----|-----------|
|0|Выполнено|
|1|Отказ|

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы импортировать записи реестра из файла с именем Аппбкуп. reg, введите:
```
reg import AppBkUp.reg
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)