---
title: Управление — автоматическое разблокирование BDE
description: Справочная статья по команде "Управление автоматическим разблокированием — BDE", которая управляет автоматической разблокировкой дисков с данными, защищенными BitLocker.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 063528bf-d235-4b44-887a-52a7d983e01a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a81d3e864a33efd5a6a1c81a5a193338d2c25bfa
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85931630"
---
# <a name="manage-bde-autounlock"></a>Управление — автоматическое разблокирование BDE

Управляет автоматическим разблокированием дисков данных, защищенных с помощью BitLocker.

## <a name="syntax"></a>Синтаксис

```
manage-bde -autounlock [{-enable|-disable|-clearallkeys}] <drive> [-computername <name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| — включить | Включает автоматическое снятие блокировки для диска данных. |
| — отключить | Отключает автоматическое снятие блокировки для диска данных. |
| -клеараллкэйс | Удаляет все сохраненные внешние ключи на диске операционной системы. |
| `<drive>` | Представляет букву диска, за которой следует двоеточие. |
| -ComputerName | Указывает, что manage-bde.exe будет использоваться для изменения защиты BitLocker на другом компьютере. Можно также использовать параметр **-CN** в качестве сокращенной версии этой команды. |
| `<name>` | Представляет имя компьютера, на котором необходимо изменить защиту BitLocker. Допустимые значения включают имя NetBIOS компьютера и IP-адрес компьютера. |
| -? или/? | Отображает краткую справку в командной строке. |
| -Help или-h | Отображает полную справку в командной строке. |

## <a name="examples"></a>Примеры

Чтобы включить автоматическую разблокировку диска данных E, введите:

```
manage-bde –autounlock -enable E:
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда Manage-bde](manage-bde.md)