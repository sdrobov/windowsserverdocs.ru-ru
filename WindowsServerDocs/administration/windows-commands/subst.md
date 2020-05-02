---
title: subst
description: Сведения о связывании пути с буквой диска.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3e69234c-2312-4343-868b-afc1017c622a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 62ba0de33e69998e7d3e343b1e53c1de7e630e10
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721611"
---
# <a name="subst"></a>subst



Связывает путь с буквой диска. При использовании без параметров **subst** отображает имена используемых виртуальных дисков.



## <a name="syntax"></a>Синтаксис

```
subst [<Drive1>: [<Drive2>:]<Path>] 
subst <Drive1>: /d
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<> диск1:|Указывает виртуальный диск, которому необходимо назначить путь.|
|[\<Диск2>:] \<> пути|Указывает физический диск и путь, который вы хотите назначить виртуальному диску.|
|/d|Удаляет подставляемый (виртуальный) диск.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

-   Следующие команды не работают и не должны использоваться на дисках, указанных в команде **subst** :

    **chkdsk**

    **diskcomp**

    **diskcopy**

    **format**

    **label**

    **recover**
-   Параметр *диск1* должен находиться в диапазоне, указанном командой **ластдриве** . В противном случае **subst** выводит следующее сообщение об ошибке:

    `Invalid parameter - drive1:`

## <a name="examples"></a><a name="BKMK_examples"></a>Примеры

Чтобы создать виртуальный диск Z для пути Б:\усер\бетти\формс, введите:
```
subst z: b:\user\betty\forms 
```
Вместо того чтобы вводить полный путь, можно получить доступ к этому каталогу, введя букву виртуального диска, а затем двоеточие, как показано ниже.
```
z: 
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)