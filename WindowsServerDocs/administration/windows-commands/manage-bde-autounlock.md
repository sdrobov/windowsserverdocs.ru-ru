---
title: Управление — автоматическое разблокирование BDE
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 063528bf-d235-4b44-887a-52a7d983e01a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1cc467c4afcfa2df344e9190a341a9aad086c1ea
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724218"
---
# <a name="manage-bde-autounlock"></a>Manage-bde: автоматическое разблокирование



Управляет автоматическим разблокированием дисков данных, защищенных с помощью BitLocker.

## <a name="syntax"></a>Синтаксис

```
manage-bde -autounlock [{-enable|-disable|-clearallkeys}] <Drive> [-computername <Name>] [{-?|/?}] [{-help|-h}]

```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|— включить|Включает автоматическое снятие блокировки для диска данных.|
|— отключить|Отключает автоматическое снятие блокировки для диска данных.|
|-клеараллкэйс|Удаляет все сохраненные внешние ключи на диске операционной системы.|
|\<> диска|Представляет букву диска, за которой следует двоеточие.|
|-ComputerName|Указывает, что Manage-bde. exe будет использоваться для изменения защиты BitLocker на другом компьютере. Можно также использовать параметр **-CN** в качестве сокращенной версии этой команды.|
|\<Name>|Представляет имя компьютера, на котором необходимо изменить защиту BitLocker. Допустимые значения включают имя NetBIOS компьютера и IP-адрес компьютера.|
|-? или/?|Отображает краткую справку в командной строке.|
|-Help или-h|Отображает полную справку в командной строке.|

## <a name="examples"></a>Примеры

Демонстрация использования команды **-разблокировки** для включения автоматической разблокировки диска данных E.
```
manage-bde –autounlock -enable E:
```

## <a name="additional-references"></a>Дополнительные ссылки

-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [Управление — BDE](manage-bde.md)