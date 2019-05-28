---
ms.assetid: 693ab895-9d0c-47c1-9f52-df5cd287842a
title: fsutil objectid
ms.prod: windows-server-threshold
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
audience: IT Pro
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: 2f5887f20e2c36ec7dcfcd6f4e920b5273c6c60c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59813745"
---
# <a name="fsutil-objectid"></a>fsutil objectid
>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows 10, Windows Server 2012 R2, Windows 8.1, Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows 7

Управляет идентификаторов объекта (OID), которые являются внутренними объектами, используемый службой отслеживания распределенных ссылку (Ленточного) клиента и службы репликации файлов (FRS) для отслеживания других объектов, таких как файлы, каталоги и ссылки. Идентификаторы объектов невидимы для большинства программ и не подлежат изменению.

> [!CAUTION]
> Не удаляйте, задать и изменить идентификатор объекта. Удаление или задание идентификатора объекта может привести к потере данных из одного файла, вплоть до целых томов данных. Кроме того может привести к нежелательным последствиям в службе отслеживания распределенных ссылку (Ленточного) клиента и службы репликации файлов (FRS).

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
fsutil objectid [create] <FileName>
fsutil objectid [delete] <FileName>
fsutil objectid [query] <FileName>
fsutil objectid [set] <ObjectID> <BirthVolumeID> <BirthObjectID> <DomainID> <FileName>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------------|---------------|
|создание|Создает идентификатор объекта, если указанный файл уже нет. Если файл уже содержит идентификатор объекта, подкоманды эквивалентен **запроса** подкоманды.|
|"Удалить"|Удаляет идентификатор объекта.|
|запрос|Запрашивает идентификатор объекта.|
|набора|Задает идентификатор объекта.|
|\<Идентификатор объекта >|Задает файл 16-разрядный шестнадцатеричный идентификатор, который гарантированно будет уникальным в пределах тома. Идентификатор объекта используется служба отслеживания распределенных ссылку (Ленточного) клиента и службы репликации файлов (FRS) для идентификации файлов.|
|\<ID_тома-источника >|Указывает, тома, на котором был расположен файл, когда он сначала получить идентификатор объекта. Это значение равно 16-разрядный шестнадцатеричный идентификатор, используемый службой Ленточного клиента.|
|\<BirthObjectID>|Указывает исходный идентификатор объекта файла ( *ObjectID* может измениться при перемещении файла). Это значение равно 16-разрядный шестнадцатеричный идентификатор, используемый службой Ленточного клиента.|
|\<Тома >|16-разрядный шестнадцатеричный идентификатор домена. Это значение в настоящий момент не используется и должно быть присвоено все нули.|
|\<Имя файла >|Указывает полный путь к файлу, включая имя файла и расширение, например C:\documents\filename.txt.|

## <a name="remarks"></a>Примечания

-   Любой файл, который содержит идентификатор объекта также имеет идентификатора тома рождения, идентификатор объекта рождения и идентификатор домена. При перемещении файла может изменить идентификатор объекта, но тома рождения и идентификаторы объектов рождения остаются теми же. Это поведение позволяет операционной системе Windows всегда найти файл, независимо от того, где он был перемещен.

## <a name="BKMK_examples"></a>Примеры
Чтобы создать идентификатор объекта, введите:

`fsutil objectid create c:\temp\sample.txt`

Чтобы удалить идентификатор объекта, введите:

`fsutil objectid delete c:\temp\sample.txt`

Чтобы запросить идентификатор объекта, введите:

`fsutil objectid query c:\temp\sample.txt`

Чтобы задать идентификатор объекта, введите:

`fsutil objectid set 40dff02fc9b4d4118f120090273fa9fc f86ad6865fe8d21183910008c709d19e 40dff02fc9b4d4118f120090273fa9fc 00000000000000000000000000000000 c:\temp\sample.txt`

#### <a name="additional-references"></a>Дополнительная справка
[Ключ синтаксиса командной строки](Command-Line-Syntax-Key.md)

[fsutil](Fsutil.md)

