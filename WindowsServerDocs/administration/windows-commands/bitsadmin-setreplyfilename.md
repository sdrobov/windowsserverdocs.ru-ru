---
title: bitsadmin setreplyfilename
description: Раздел команд Windows для **битсадмин сетреплифиленаме**, который указывает путь к файлу, содержащему сервер отправка-ответ.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c26d3342-0533-40b1-a13e-e09678232b25
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6c476073cb22ff66bcefc75a45fcd0526cdf3d25
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81122738"
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
| задания | Отображаемое имя задания или идентификатор GUID. |
| file_path | Расположение для отправки и ответа сервера. |

## <a name="examples"></a>Примеры

В следующем примере задается путь к файлу имени файла для задания передачи и ответа с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /setreplyfilename myDownloadJob c:\upload-reply
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)