---
title: mklink
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0ce4df22-2dbc-48fc-9c16-b721ae85f857
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3d6328d972b07b1bebd272788b896fd491e47380
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80839557"
---
# <a name="mklink"></a>mklink
Создает символьную ссылку.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

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
|> ссылки \<|Указывает имя создаваемой символьной ссылки.|
|Целевой > \<|Указывает путь (относительный или абсолютный), на который ссылается Новая символьная ссылка.|
|/?|Отображает справку в командной строке.|

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере демонстрируется создание и удаление символьной ссылки с именем MyFolder и MyFile. file из корневого каталога в каталог \Users\User1\Documents и файл example. File, находящийся в каталоге:
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
