---
title: Управление — BDE чанжекэй
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 69463db9-7e03-47ff-b233-a95d5055725f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6b5f152e4e98387adb7e7780f8458edd409b1a9d
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724203"
---
# <a name="manage-bde-changekey"></a>Manage-bde: чанжекэй



Изменяет ключ запуска для диска операционной системы.

## <a name="syntax"></a>Синтаксис

```
manage-bde -changekey [<Drive>] [<PathToExternalKeyDirectory>] [-computername <Name>] [{-?|/?}] [{-help|-h}]
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<> диска|Представляет букву диска, за которой следует двоеточие.|
|\<Пастоекстерналкэйдиректори>|Представляет расположение каталога, в котором сохраняется внешний файл ключа запуска, который можно использовать для разблокировки диска.|
|-ComputerName|Указывает, что Manage-bde. exe будет использоваться для изменения защиты BitLocker на другом компьютере. Можно также использовать параметр **-CN** в качестве сокращенной версии этой команды.|
|\<Name>|Представляет имя компьютера, на котором необходимо изменить защиту BitLocker. Допустимые значения включают имя NetBIOS компьютера и IP-адрес компьютера.|
|-? или/?|Отображает краткую справку в командной строке.|
|-Help или-h|Отображает полную справку в командной строке.|

## <a name="examples"></a>Примеры

Демонстрация использования команды **-чанжекэй** для создания нового ключа запуска на диске E для использования с шифрованием BitLocker на диске C.
```
manage-bde -changekey C: E:\
```

## <a name="additional-references"></a>Дополнительные ссылки

-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [Управление — BDE](manage-bde.md)
