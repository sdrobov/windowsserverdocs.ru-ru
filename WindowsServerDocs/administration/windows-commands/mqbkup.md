---
title: mqbkup
description: Справочная статья по команде мкбкуп, которая создает резервную копию файлов сообщений MSMQ и параметров реестра на устройстве хранения и восстанавливает ранее сохраненные сообщения и параметры.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7bdd41c4-75ef-455f-b241-1d64a4c7acf5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 00518ab36f1886ccb3a1221a065715668fb02f47
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86956926"
---
# <a name="mqbkup"></a>mqbkup

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Резервное копирование файлов сообщений MSMQ и параметров реестра на запоминающее устройство и восстановление ранее сохраненных сообщений и параметров.

Операции резервного копирования и восстановления останавливают локальную службу MSMQ. Если служба MSMQ была запущена заранее, она попытается перезапустить службу MSMQ по завершении операции резервного копирования или восстановления. Если служба уже была остановлена перед запуском программы, то перезагрузка службы не выполняется.

Перед использованием программы архивации и восстановления MSMQ Message необходимо закрыть все локальные приложения, использующие MSMQ.

## <a name="syntax"></a>Синтаксис

```
mqbkup {/b | /r} <folder path_to_storage_device>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| ------- | -------- |
| /b | Указывает операцию резервного копирования. |
| /r | Указывает операцию восстановления. |
| `<folder path_to_storage_device>` | Указывает путь, по которому хранятся файлы сообщений MSMQ и параметры реестра. |
| /? | Отображение справки в командной строке. |

#### <a name="remarks"></a>Комментарии

- Если указанная папка не существует при выполнении операции резервного копирования или восстановления, то эта папка автоматически создается программой.

- Если вы решили указать существующую папку, она должна быть пустой. Если указать непустую папку, программа удалит каждый файл и вложенную папку, содержащиеся в ней. В этом случае вам будет предложено предоставить разрешение на удаление существующих файлов и вложенных папок. Параметр **/y** можно использовать, чтобы указать, что вы соглашаетесь с удалением всех существующих файлов и вложенных папок в указанной папке.

- Расположение папок, используемых для хранения файлов сообщений MSMQ, хранится в реестре. Таким образом, программа восстанавливает файлы сообщений MSMQ в папки, указанные в реестре, а не в папки хранилища, используемые перед операцией восстановления.

### <a name="examples"></a>Примеры

Чтобы создать резервную копию всех файлов сообщений MSMQ и параметров реестра и сохранить их в папке *мсмкбкуп* на диске C:, введите:

```
mqbkup /b c:\msmqbkup
```

Чтобы удалить все существующие файлы и вложенные папки в папке *олдбкуп* на диске C:, а затем сохранить файлы сообщений MSMQ и параметры реестра в папке, введите:

```
mqbkup /b /y c:\oldbkup
```

Чтобы восстановить сообщения и параметры реестра MSMQ, введите:

```
mqbkup /r c:\msmqbkup
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Справочник по MSMQ PowerShell](/powershell/module/msmq/?view=win10-ps)
