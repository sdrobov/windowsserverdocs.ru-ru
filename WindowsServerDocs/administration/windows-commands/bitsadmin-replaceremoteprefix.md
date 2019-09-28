---
title: bitsadmin replaceremoteprefix
description: Раздел команд Windows для **битсадмин реплацеремотепрефикс** . все файлы в задании, для которых удаленный URL-адрес начинается с *олдпрефикс* , изменены для использования *невпрефикс*.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d0e0abb1-bdb4-4c74-abbc-16c809f5fd81
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ee896a337b571487797967d3ce0bf1f1b17e7507
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380801"
---
# <a name="bitsadmin-replaceremoteprefix"></a>bitsadmin replaceremoteprefix

Все файлы в задании с удаленным URL-адресом, начинающимся с *олдпрефикс* , изменяются для использования *невпрефикс*.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /ReplaceRemotePrefix <Job> <OldPrefix> <NewPrefix
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|
|олдпрефикс|Существующий префикс URL-адреса|
|невпрефикс|Новый префикс URL-адреса|

## <a name="examples"></a>Примеры

В следующем примере изменяются все файлы в задании с именем *мидовнлоаджоб* , для которых удаленный URL-адрес начинается с *http://stageserver* до *http://prodserver* .

```
C:\>bitsadmin /ReplaceRemotePrefix myDownloadJob http://stageserver http://prodserver
```

## <a name="additional-information"></a>Дополнительные сведения

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)