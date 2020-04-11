---
title: bitsadmin setnotifycmdline
description: Раздел команд Windows для **битсадмин сетнотификмдлине**, который задает команду командной строки, которая будет выполняться, когда задание завершает передачу данных или когда задание переходит в состояние.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 415ae6ef-8549-48b2-9693-2368a6e24075
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b268b68cbd355a7fe7f993d678a98f6fcb99f0ab
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81122898"
---
# <a name="bitsadmin-setnotifycmdline"></a>bitsadmin setnotifycmdline

Задает команду командной строки, которая будет запускаться, когда задание завершает передачу данных или когда задание переходит в указанное состояние.

> [!NOTE]
> Эта команда не поддерживается в БИТАХ 1,2 и более ранних версиях.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /setnotifycmdline <job> <program_name> [program_parameters]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| задания | Отображаемое имя задания или идентификатор GUID. |
| program_name | Имя команды, выполняемой по завершении задания. Это значение можно задать как NULL, но в этом случае *program_parameters* также должно иметь значение null. |
| program_parameters | Параметры, которые необходимо передать в *program_name*. Это значение можно задать как NULL. Если *program_parameters* не имеет значение null, первый параметр в *program_parameters* должен соответствовать *program_name*. |

## <a name="examples"></a>Примеры

В следующем примере задается команда командной строки, используемая службой для запуска Notepad. exe после завершения задания с именем *мидовнлоаджоб* .

```
C:\>bitsadmin /setnotifycmdline myDownloadJob c:\winnt\system32\notepad.exe NULL
```

```
C:\>bitsadmin /setnotifycmdline myDownloadJob c:\winnt\system32\notepad.exe notepad c:\eula.txt
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)