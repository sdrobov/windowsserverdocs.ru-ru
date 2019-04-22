---
title: bitsadmin create
description: Раздел Windows команды для **bitsadmin создать** -создает задание передачи с помощью заданного отображаемое имя.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9a8c53af-900b-4c24-9265-5b8b08213fac
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d6ce5a4fdc21d879bf0a265e3c4185d83311464a
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59817195"
---
# <a name="bitsadmin-create"></a>bitsadmin create

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Создает задание передачи с помощью заданного отображаемое имя. Скачивание заданий передачи данных с сервера в локальный файл. Отправка заданий передачи данных из локального файла на сервер. Задания отправки ответа передачи данных из локального файла на сервер и получать от сервера ответный файл.

Используйте [bitsadmin resume](bitsadmin-resume.md) коммутатора, чтобы активировать задание в очереди передачи.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /create [type] DisplayName
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------|--------|
|type|-   **/ Скачать** передает данные с сервера в локальный файл.<br />-   **/ Отправить** передает данные из локального файла на сервер.<br />-   **/ Отправки-ответа** передает данные из локального файла на сервер и получает файл ответа с сервера.<br />-Значение по умолчанию **/скачать** Если не указан в командной строке.|
|DisplayName|Отображаемое имя, назначенное для вновь созданного задания.|

**БИТЫ 1.2 и более ранних версий**: / Upload и /Upload-Reply типы недоступны.

## <a name="BKMK_examples"></a>Примеры

Создается задание загрузки *myDownloadJob*.

```
C:\>bitsadmin /create myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

[Ключ синтаксиса командной строки](command-line-syntax-key.md)
