---
title: bitsadmin create
description: Справочная статья по команде битсадмин Create, которая создает задание перемещения с заданным отображаемым именем.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9a8c53af-900b-4c24-9265-5b8b08213fac
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b3e0f8fb7d8396a238cabcbeb375f61cbe526c3f
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85928342"
---
# <a name="bitsadmin-create"></a>bitsadmin create

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Создает задание перемещения с заданным отображаемым именем.

> [!NOTE]
> **/Upload**   Типы параметров/upload и **/уплоад-репли** не поддерживаются в битах 1,2 и более ранних версиях.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /create [type] displayname
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| ------- | -------- |
| type | Существует три типа заданий:<ul><li>**Обновление.** Передает данные с сервера в локальный файл.</li><li>**Дают.** Передает данные из локального файла на сервер.</li><li>**/уплоад-репли.** Передает данные из локального файла на сервер и получает ответный файл с сервера.</li></ul>Если этот параметр не задан, по умолчанию используется значение **/download** . |
| displayname | Отображаемое имя, назначенное только что созданному заданию. |

## <a name="examples"></a>Примеры

Чтобы создать задание загрузки с именем *мидовнлоаджоб*, выполните следующие действия.

```
bitsadmin /create myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда возобновления битсадмин](bitsadmin-resume.md)

- [Команда битсадмин](bitsadmin.md)
