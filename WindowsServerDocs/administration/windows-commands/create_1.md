---
title: create
description: Справочный раздел по созданию, который запускает процесс создания теневой копии с использованием текущего контекста и настроек параметров.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 837aa449-9b60-41ae-9ef1-ef67af6e5918
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: cfddbebd5744d8cd222d67e46690ce8b5d2e0fde
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82716836"
---
# <a name="create"></a>create

Запускает процесс создания теневой копии с использованием текущего контекста и настроек параметров. Требуется по крайней мере один том в наборе теневых копий.

## <a name="syntax"></a>Синтаксис

```
create
```

## <a name="remarks"></a>Примечания

-   Перед использованием команды " **создать** " необходимо добавить по крайней мере один том с помощью команды " **Добавить том** ".
-   Чтобы указать полную резервную копию, а не резервную копию, можно использовать команду **начать резервное** копирование.
-   После выполнения команды **CREATE** можно использовать команду **exec** , чтобы выполнить повторяющийся скрипт для резервного копирования из теневой копии.

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)