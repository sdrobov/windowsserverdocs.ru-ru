---
title: bitsadmin create
description: Раздел команд Windows для **битсадмин Create**, который создает задание перемещения с заданным отображаемым именем.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9a8c53af-900b-4c24-9265-5b8b08213fac
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4a922d9f15aff0a9bd064a7e987920adf3a9107d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850817"
---
# <a name="bitsadmin-create"></a>bitsadmin create

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Создает задание перемещения с заданным отображаемым именем. Загрузка заданий передавать данные с сервера в локальный файл. Отправка заданий передача данных из локального файла на сервер. Задания отправки и ответа передают данные из локального файла на сервер и получают файл ответов с сервера.

Используйте параметр [возобновления битсадмин](bitsadmin-resume.md) , чтобы активировать задание в очереди на перемещение.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /create [type] displayname
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| ------- | -------- |
| тип | -  **/download** передает данные с сервера в локальный файл.<p>-  **/upload** передает данные из локального файла на сервер.<p>-  **/уплоад-репли** передает данные из локального файла на сервер и получает ответный файл с сервера.<p>По умолчанию этот параметр имеет значение **/download** , если не указано в командной строке. Кроме того, типы  **/Upload** и **/УПЛОАД-РЕПЛИ** недоступны в битах 1,2 и более ранних версиях. |
| displayName | Отображаемое имя, назначенное только что созданному заданию. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Создает задание скачивания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /create myDownloadJob
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
