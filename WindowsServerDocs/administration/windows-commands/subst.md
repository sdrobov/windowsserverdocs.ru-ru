---
title: subst
description: Сведения о связывании пути с буквой диска.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: f3010d1e58fbd360b8311512e6664873b020c12b
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71383755"
---
# <a name="subst"></a>subst



Связывает путь с буквой диска. При использовании без параметров **subst** отображает имена используемых виртуальных дисков.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
subst [<Drive1>: [<Drive2>:]<Path>] 
subst <Drive1>: /d
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|> \<диск1:|Указывает виртуальный диск, которому необходимо назначить путь.|
|[\<диск2 >:]\<путь >|Указывает физический диск и путь, который вы хотите назначить виртуальному диску.|
|/d|Удаляет подставляемый (виртуальный) диск.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Замечания

-   Следующие команды не работают и не должны использоваться на дисках, указанных в команде **subst** :

    **chkdsk**

    **diskcomp**

    **diskcopy**

    **format**

    **label**

    **recover**
-   Параметр *диск1* должен находиться в диапазоне, указанном командой **ластдриве** . В противном случае **subst** выводит следующее сообщение об ошибке:

    `Invalid parameter - drive1:`

## <a name="BKMK_examples"></a>Примеров

Чтобы создать виртуальный диск Z для пути B:\user\betty\forms, введите:
```
subst z: b:\user\betty\forms 
```
Вместо того чтобы вводить полный путь, можно получить доступ к этому каталогу, введя букву виртуального диска, а затем двоеточие, как показано ниже.
```
z: 
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)