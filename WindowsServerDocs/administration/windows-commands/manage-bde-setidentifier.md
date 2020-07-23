---
title: Управление — BDE сетидентифиер
description: Справочная статья по команде Manage-bde сетидентифиер, которая задает в поле идентификатор диска значение, указанное в поле укажите уникальные идентификаторы для вашей организации групповая политика параметр.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7092d18f-4ac9-4c73-a20f-1246ca60e75e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c6a04b4f7c04174158a165cf0d41493078af0056
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86957046"
---
# <a name="manage-bde-setidentifier"></a>Управление — BDE сетидентифиер

Задает для поля "идентификатор диска" значение, указанное в поле **Укажите уникальные идентификаторы для вашей организации** групповая политика параметр.

## <a name="syntax"></a>Синтаксис

```
manage-bde –setidentifier <drive> [-computername <name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<drive>` | Представляет букву диска, за которой следует двоеточие. |
| -ComputerName | Указывает, что manage-bde.exe будет использоваться для изменения защиты BitLocker на другом компьютере. Можно также использовать параметр **-CN** в качестве сокращенной версии этой команды. |
| `<name>` | Представляет имя компьютера, на котором необходимо изменить защиту BitLocker. Допустимые значения включают имя NetBIOS компьютера и IP-адрес компьютера. |
| -? или/? | Отображает краткую справку в командной строке. |
| -Help или-h | Отображает полную справку в командной строке. |

### <a name="examples"></a>Примеры

Чтобы задать поле идентификатора диска BitLocker для C, введите:

```
manage-bde –setidentifier C:
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда Manage-bde](manage-bde.md)

- [Руководство по восстановлению BitLocker](/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan)
