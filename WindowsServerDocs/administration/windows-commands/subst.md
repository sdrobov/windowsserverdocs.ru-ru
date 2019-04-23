---
title: subst
description: Узнайте, как связать путь с буквой диска.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3e69234c-2312-4343-868b-afc1017c622a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 858195de89ca8661cf47c25b6cf9b519cc4efbf8
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59858075"
---
# <a name="subst"></a>subst



Связывает путь с буквой диска. При использовании без параметров, **subst** фактически имена виртуальных дисков.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
subst [<Drive1>: [<Drive2>:]<Path>] 
subst <Drive1>: /d
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Диск1 >:|Указывает виртуальный диск, к которому вы хотите назначить путь.|
|[\<Диск2 >:]\<путь >|Задает физический диск и путь, который вы хотите назначить в качестве виртуального диска.|
|/d|Удаляет замененный виртуального диска.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

-   Следующие команды, не работают и не должны использоваться на дисках, которые указаны в **subst** команды:

    **CHKDSK**

    **экран будет**

    **diskcopy**

    **Формат**

    **Метка**

    **Восстановление**
-   *Диск1* параметр должен быть в диапазоне, который задается параметром **lastdrive** команды. В противном случае **subst** отображает следующее сообщение об ошибке:

    `Invalid parameter - drive1:`

## <a name="BKMK_examples"></a>Примеры

Чтобы создать виртуальный диск Z путь B:\User\Betty\Forms, введите следующую команду:
```
subst z: b:\user\betty\forms 
```
Вместо того чтобы вводить полный путь, вы может получить доступ к каталогу, введя имя виртуального диска, за которым следует двоеточие следующим образом:
```
z: 
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)