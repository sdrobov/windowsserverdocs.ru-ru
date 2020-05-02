---
title: bitsadmin setnotifycmdline
description: Справочный раздел по команде битсадмин сетнотификмдлине, который задает команду командной строки, которая будет запускаться, когда задание завершает передачу данных или когда задание переходит в состояние.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 415ae6ef-8549-48b2-9693-2368a6e24075
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b21d7151a5b646a4fe07d073220614f5e3c99539
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720132"
---
# <a name="bitsadmin-setnotifycmdline"></a>bitsadmin setnotifycmdline

Задает команду командной строки, которая запускается после того, как задание завершает передачу данных, или после того, как задание переходит в указанное состояние.

> [!NOTE]
> Эта команда не поддерживается в БИТАХ 1,2 и более ранних версиях.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /setnotifycmdline <job> <program_name> [program_parameters]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| задание | Отображаемое имя задания или идентификатор GUID. |
| program_name | Имя команды, выполняемой по завершении задания. Это значение можно задать как NULL, но в этом случае *program_parameters* также должно иметь значение null. |
| program_parameters | Параметры, которые необходимо передать в *program_name*. Это значение можно задать как NULL. Если *program_parameters* не имеет значение null, первый параметр в *program_parameters* должен соответствовать *program_name*. |

## <a name="examples"></a>Примеры

Чтобы запустить Notepad. exe по завершении задания с именем *мидовнлоаджоб*:

```
bitsadmin /setnotifycmdline myDownloadJob c:\winnt\system32\notepad.exe NULL
```

Чтобы отобразить текст лицензионного соглашения в Notepad. exe по завершении задания с именем Мидовнлоаджоб:

```
bitsadmin /setnotifycmdline myDownloadJob c:\winnt\system32\notepad.exe notepad c:\eula.txt
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
