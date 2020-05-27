---
title: Manage-bde ChangePassword
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b174e152-8442-4fba-8b33-56a81ff4f547
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d29b5e9c3b85eb914c9ce66f9798a0f222183bdf
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83820704"
---
# <a name="manage-bde-changepassword"></a>Manage-bde: ChangePassword



Изменяет пароль для диска данных. Пользователю будет предложено ввести новый пароль.

## <a name="syntax"></a>Синтаксис

```
manage-bde -changepassword [<Drive>] [-computername <Name>] [{-?|/?}] [{-help|-h}]
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<> диска|Представляет букву диска, за которой следует двоеточие.|
|-ComputerName|Указывает, что Manage-bde. exe будет использоваться для изменения защиты BitLocker на другом компьютере. Можно также использовать параметр **-CN** в качестве сокращенной версии этой команды.|
|\<Name>|Представляет имя компьютера, на котором необходимо изменить защиту BitLocker. Допустимые значения включают имя NetBIOS компьютера и IP-адрес компьютера.|
|-? или/?|Отображает краткую справку в командной строке.|
|-Help или-h|Отображает полную справку в командной строке.|

## <a name="examples"></a>Примеры

Демонстрация использования команды **-ChangePassword** для изменения пароля, используемого для разблокировки BitLocker на диске данных D.
```
manage-bde –changepassword D:
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [Управление — BDE](manage-bde.md)