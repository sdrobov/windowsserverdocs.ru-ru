---
title: ksetup removerealm
description: Справочная статья по команде ksetup ремовереалм, которая удаляет из реестра все сведения об указанной области.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 39f0c6f0-4c50-4781-941e-0893495405e8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0330f7b5f9121da2fce99985fe116be46eb1c9d9
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85933663"
---
# <a name="ksetup-removerealm"></a>ksetup removerealm

Удаляет из реестра все сведения для указанной области.

Имя области сохраняется в реестре в `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001` и `\CurrentControlSet\Control\Lsa\Kerberos` . Эта запись не существует в реестре по умолчанию. Для заполнения реестра можно использовать команду [ksetup аддреалмфлагс](ksetup-addrealmflags.md) .

> [!IMPORTANT]
> Нельзя удалить имя сферы по умолчанию из контроллера домена, так как это приведет к сбросу данных DNS, а удаление может привести к невозможности использования контроллера домена.

## <a name="syntax"></a>Синтаксис

```
ksetup /removerealm <realmname>
```
### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<realmname>` | Указывает DNS-имя в верхнем регистре, например CORP. CONTOSO.COM и указывается в качестве области по умолчанию или **области =** при запуске **ksetup** . |

### <a name="examples"></a>Примеры

Удаление ошибочного имени области (. CON вместо. COM) с локального компьютера, введите:
```
ksetup /removerealm CORP.CONTOSO.CON
```

Чтобы проверить удаление, можно выполнить команду **ksetup** и проверить выходные данные.

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда ksetup](ksetup.md)

- [ksetup сетреалм, команда](ksetup-setrealm.md)
