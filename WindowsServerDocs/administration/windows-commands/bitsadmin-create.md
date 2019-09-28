---
title: bitsadmin create
description: Раздел команд Windows для **битсадмин Create** — создает задание перемещения с заданным отображаемым именем.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 9f6d641d44c56ea4ff11f48a725367de7dcf472a
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381806"
---
# <a name="bitsadmin-create"></a>bitsadmin create

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Создает задание перемещения с заданным отображаемым именем. Загрузка заданий передавать данные с сервера в локальный файл. Отправка заданий передача данных из локального файла на сервер. Задания отправки и ответа передают данные из локального файла на сервер и получают файл ответов с сервера.

Используйте параметр [возобновления битсадмин](bitsadmin-resume.md) , чтобы активировать задание в очереди на перемещение.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /create [type] DisplayName
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------|--------|
|type|-    **/download** передает данные с сервера в локальный файл.<br />-    **/upload** передает данные из локального файла на сервер.<br />-    **/уплоад-репли** передает данные из локального файла на сервер и получает ответный файл с сервера.<br />— Этот параметр по умолчанию имеет значение **/download** , если не указано в командной строке.|
|DisplayName|Отображаемое имя, назначенное только что созданному заданию.|

**BITS 1,2 и более ранних версий**: Типы/upload и/Уплоад-репли недоступны.

## <a name="BKMK_examples"></a>Примеров

Создает задание скачивания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /create myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
