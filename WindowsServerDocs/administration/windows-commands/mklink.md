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
ms.openlocfilehash: 83a607711f0abe51810aa5abf4eb731206d810c2
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723974"
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
## <a name="additional-references"></a>Дополнительная справка
-   [Новый элемент](https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-item?view=powershell-6)
-   [del](https://docs.microsoft.com/windows-server/administration/windows-commands/del)
-   [rmdir](https://docs.microsoft.com/windows-server/administration/windows-commands/rd)
