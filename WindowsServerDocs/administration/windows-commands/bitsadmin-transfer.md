---
title: bitsadmin Transfer
description: Раздел Windows команды для **bitsadmin передачи** -передает один или несколько файлов.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fe302141-b33a-4a05-835e-dc4fc4db7d5a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2ef29a242a834fae42d1de3994a82aedcf87ec2d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59852465"
---
# <a name="bitsadmin-transfer"></a>bitsadmin Transfer

Передает один или несколько файлов. Чтобы перенести несколько файлов, указать несколько \<RemoteFileName\>-\<LocalFileName\> пары. Пар, разделенных пробелами.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /Transfer <Name> [<Type>] [/Priority <Job_Priority>] [/ACLFlags <Flags>] [/DYNAMIC] <RemoteFileName> <LocalFileName>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Имя|Имя задания. В отличие от большинства команд **имя** возможно только в том случае, имя и не является GUID.|
|Тип|Необязательно: Укажите тип задания. Используйте **/СКАЧАТЬ** (по умолчанию) для задания скачивания или **/отправить** для отправки задания.|
|Priority|Необязательно — job_priority присвоено одно из следующих значений:</br>-ПЕРЕДНЕГО ПЛАНА</br>-ВЫСОКИЙ</br>-НОРМ.</br>-LOW|
|ACLFlags|Необязательно — указывает, что для поддержки владельца и данные ACL с загружаемый файл. Например, для поддержания владельца и группу с файлом, можно задать флаги `OG`. Укажите одно или несколько из следующих флагов:</br>-O: Скопируйте сведения о владельце с файлом.</br>-   G: Скопируйте сведения о группах с файлом.</br>-D: Скопируйте сведения DACL с файлом.</br>-   S: Скопируйте сведения системный список управления ДОСТУПОМ с файлом.|
|\/ДИНАМИЧЕСКИЕ|Настраивает задание с [ **BITS_JOB_PROPERTY_DYNAMIC_CONTENT**](/windows/desktop/api/bits5_0/ne-bits5_0-bits_job_property_id), что снижает требования на стороне сервера.|
|RemoteFileName|Имя файла, при передаче на сервер.|
|LocalFileName|Имя файла, который размещается локально.|

## <a name="remarks"></a>Примечания

По умолчанию служба BITSAdmin создает задание загрузки, которое выполняется в **ОБЫЧНЫЙ** приоритет и обновляет сведения о ходе выполнения командное окно до завершения передачи или пока не возникает критическая ошибка. Служба завершает задание, если он успешно передает все файлы и отменяет задание, если возникает критическая ошибка. Служба не выполняет задания, если это не удается добавить файлы в задание, или если указано недопустимое значение для *тип* или *Job_Priority*. Чтобы перенести несколько файлов, указать несколько *RemoteFileName*-*LocalFileName* пары. Пар, разделенных пробелами.

> [!NOTE]
> Команда BITSAdmin продолжает выполняться, если возникает временная ошибка. Чтобы завершить команду, нажмите клавиши CTRL + C.

## <a name="BKMK_examples"></a>Примеры

Следующий пример начинается, передачи задания с именем *myDownloadJob*.
```
C:\>bitsadmin /Transfer myDownloadJob http://prodserver/audio.wma c:\downloads\audio.wma
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)