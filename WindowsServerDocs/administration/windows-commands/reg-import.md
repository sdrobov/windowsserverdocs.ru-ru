---
title: импорт реестра
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0be103de-08fc-4f02-b590-361782680b3e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3e7e033091752f97086fd27fcb94e62469f0cced
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82722555"
---
# <a name="reg-import"></a>импорт реестра



Копирует содержимое файла, содержащего экспортированные подразделы, записи и значения реестра, в реестр локального компьютера.



## <a name="syntax"></a>Синтаксис

```
Reg import FileName
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Имя файла>|Указывает имя и путь к файлу, который содержит содержимое, копируемое в реестр локального компьютера. Этот файл должен быть создан заранее с помощью команды **reg export**.|
|/?|Отображает справку по **импорту реестра** в командной строке.|

## <a name="remarks"></a>Примечания

В следующей таблице перечислены возвращаемые значения для операции **reg import** .

|Значение|Описание|
|-----|-----------|
|0|Успех|
|1|Сбой|

## <a name="examples"></a>Примеры

Чтобы импортировать записи реестра из файла с именем Аппбкуп. reg, введите:
```
reg import AppBkUp.reg
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)