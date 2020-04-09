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
ms.openlocfilehash: 43cbc57aba29ea0b9150dccdfc566a93017a09a5
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80833647"
---
# <a name="subst"></a>subst



Связывает путь с буквой диска. При использовании без параметров **subst** отображает имена используемых виртуальных дисков.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
subst [<Drive1>: [<Drive2>:]<Path>] 
subst <Drive1>: /d
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|> \<диск1:|Указывает виртуальный диск, которому необходимо назначить путь.|
|[\<диск2 >:]\<путь >|Указывает физический диск и путь, который вы хотите назначить виртуальному диску.|
|/d|Удаляет подставляемый (виртуальный) диск.|
|/?|Отображает справку в командной строке.|

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

## <a name="examples"></a><a name="BKMK_examples"></a>Примеров

Чтобы создать виртуальный диск Z для пути Б:\усер\бетти\формс, введите:
```
subst z: b:\user\betty\forms 
```
Вместо того чтобы вводить полный путь, можно получить доступ к этому каталогу, введя букву виртуального диска, а затем двоеточие, как показано ниже.
```
z: 
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)