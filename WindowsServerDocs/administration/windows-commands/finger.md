---
title: finger
description: Справочная статья по команде finger, которая отображает сведения о пользователях на указанном удаленном компьютере, на котором запущена служба или управляющая программа Finger.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 907ea637-5c6c-4752-84c2-46bbf2a68a33
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fd629374b601686e91e5238ae8db060e0b6bf0f8
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85922425"
---
# <a name="finger"></a>finger

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает сведения о пользователях на указанном удаленном компьютере (обычно это компьютер под управлением UNIX), на котором работает служба или управляющая программа Finger. Удаленный компьютер указывает формат и выходные данные для вывода сведений о пользователе. При использовании без параметров **палец** выводит справку.

> [!IMPORTANT]
> Эта команда доступна, только если протокол Internet Protocol (TCP/IP) установлен в качестве компонента в свойствах сетевого адаптера в окне Сетевые подключения.

## <a name="syntax"></a>Синтаксис

```
finger [-l] [<user>] [@<host>] [...]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| -l | Отображает сведения о пользователе в длинном формате списка. |
| `<user>` | Указывает пользователя, сведения о котором требуется получить. Если параметр *User* не задан, эта команда отображает сведения обо всех пользователях на указанном компьютере. |
| `@<host>` | Указывает удаленный компьютер, на котором запущена служба Finger, где вы ищете сведения о пользователе. Можно указать имя или IP-адрес компьютера. |
| /? | Отображение справки в командной строке. |

#### <a name="remarks"></a>Комментарии

- Необходимо **Добавить префиксные** параметры с дефисом (-), а не косой чертой (/).

- `user@host`Можно указать несколько параметров.

### <a name="examples"></a>Примеры

Чтобы отобразить сведения для пользователя *User1* на компьютере *Users.Microsoft.com*, введите:

```
finger user1@users.microsoft.com
```

Чтобы отобразить сведения для *всех пользователей* на компьютере *Users.Microsoft.com*, введите:

```
finger @users.microsoft.com
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
