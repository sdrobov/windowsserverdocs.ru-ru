---
title: mklink
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0ce4df22-2dbc-48fc-9c16-b721ae85f857
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e4bfa1c928b5bc5f4c5a885378f0f1d1c9b99cf5
ms.sourcegitcommit: bf887504703337f8ad685d778124f65fe8c3dc13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2020
ms.locfileid: "83437139"
---
# <a name="mklink"></a>mklink
Создает символьную ссылку.



## <a name="syntax"></a>Синтаксис

```
mklink [[/d] | [/h] | [/j]] <Link> <Target>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/d|Создает символьную ссылку каталога. По умолчанию **Mklink** создает символьную ссылку на файл.|
|/h|Создает жесткую связь вместо символьной ссылки.|
|/j|Создает соединение с каталогом.|
|\<Ссылка>|Указывает имя создаваемой символьной ссылки.|
|\<Target>|Указывает путь (относительный или абсолютный), на который ссылается Новая символьная ссылка.|
|/?|Отображение справки в командной строке.|

## <a name="examples"></a>Примеры

Для демонстрации создания и удаления символьной ссылки с именем MyFolder и MyFile. file из корневого каталога в каталог \Users\User1\Documents и файл example. File, находящийся в каталоге:
```
mklink /d \MyFolder \Users\User1\Documents
mklink /h \MyFile.file \User1\Documents\example.file
rd \MyFolder
del \MyFile.file
```
## <a name="additional-references"></a>Дополнительные ссылки
-   [Новый элемент](https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-item?view=powershell-6)
-   [del](https://docs.microsoft.com/windows-server/administration/windows-commands/del)
-   [rmdir](https://docs.microsoft.com/windows-server/administration/windows-commands/rd)
