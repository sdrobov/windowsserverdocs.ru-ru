---
title: bitsadmin setreplyfilename
description: Справочная статья по команде битсадмин сетреплифиленаме, которая указывает путь к файлу, содержащему сервер отправка-ответ.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c26d3342-0533-40b1-a13e-e09678232b25
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 45582035ed986e50129e894fbabaffde5b219548
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927561"
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
