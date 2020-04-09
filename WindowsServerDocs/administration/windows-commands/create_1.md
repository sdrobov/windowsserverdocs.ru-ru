---
title: создание
description: Раздел команд Windows для инструкции CREATE, запускающий процесс создания теневой копии с использованием текущего контекста и настроек параметров.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 837aa449-9b60-41ae-9ef1-ef67af6e5918
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4d29285517ca678a15828079c95663fc4d501eaf
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80846837"
---
# <a name="create"></a>создание

Запускает процесс создания теневой копии с использованием текущего контекста и настроек параметров. Требуется по крайней мере один том в наборе теневых копий.

## <a name="syntax"></a>Синтаксис

```
create
```

## <a name="remarks"></a>Примечания

-   Перед использованием команды " **создать** " необходимо добавить по крайней мере один том с помощью команды " **Добавить том** ".
-   Чтобы указать полную резервную копию, а не резервную копию, можно использовать команду **начать резервное** копирование.
-   После выполнения команды **CREATE** можно использовать команду **exec** , чтобы выполнить повторяющийся скрипт для резервного копирования из теневой копии.

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)