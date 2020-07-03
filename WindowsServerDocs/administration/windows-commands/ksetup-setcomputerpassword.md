---
title: ksetup setcomputerpassword
description: Справочная статья по команде ksetup сеткомпутерпассворд, которая задает пароль для локального компьютера.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e307d8f6-3b93-4c24-ac04-f31549f7dc7d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 70af854838e439532e49d6159b010e453d339244
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85922617"
---
# <a name="ksetup-setcomputerpassword"></a>ksetup setcomputerpassword

Задает пароль для локального компьютера. Эта команда влияет только на учетную запись компьютера и требует перезагрузки, чтобы изменение пароля вступило в силу.

> [!IMPORTANT]
> Пароль учетной записи компьютера не отображается в реестре или в качестве выходных данных команды **ksetup** .

## <a name="syntax"></a>Синтаксис

```
ksetup /setcomputerpassword <password>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<password>` | Указывает указанный пароль для установки учетной записи компьютера на локальном компьютере. Пароль можно задать только с помощью учетной записи с правами администратора, а пароль должен содержать от 1 до 156 букв и специальных символов. |

### <a name="examples"></a>Примеры

Чтобы изменить пароль учетной записи компьютера на локальном компьютере с *IPops897* на *ИПОП $897!*, введите:

```
ksetup /setcomputerpassword IPop$897!
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда ksetup](ksetup.md)
