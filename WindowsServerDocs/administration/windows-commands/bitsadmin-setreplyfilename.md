---
title: bitsadmin setreplyfilename
description: Справочный раздел по команде битсадмин сетреплифиленаме, который указывает путь к файлу, содержащему сервер отправка-ответ.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c26d3342-0533-40b1-a13e-e09678232b25
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2f0bd184db274dc915817ff3e26ae2c686190c27
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720481"
---
# <a name="bitsadmin-setreplyfilename"></a>bitsadmin setreplyfilename

Указывает путь к файлу, содержащему сервер отправка-ответ.

> [!NOTE]
> Эта команда не поддерживается в БИТАХ 1,2 и более ранних версиях.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /setreplyfilename <job> <file_path>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задание | Отображаемое имя задания или идентификатор GUID. |
| file_path | Расположение для отправки и ответа сервера. |

## <a name="examples"></a>Примеры

Чтобы задать путь к файлу имени файла для задания upload-Reply, выполните команду с именем *мидовнлоаджоб*:

```
bitsadmin /setreplyfilename myDownloadJob c:\upload-reply
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
