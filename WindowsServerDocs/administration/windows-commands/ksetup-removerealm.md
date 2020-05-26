---
title: ksetup ремовереалм
description: Справочный раздел по команде ksetup ремовереалм, который удаляет из реестра все сведения для указанной области.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 39f0c6f0-4c50-4781-941e-0893495405e8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5da1be77a3b585e566bfd3b051b2fb391b326f32
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83817614"
---
# <a name="ksetup-removerealm"></a>ksetup ремовереалм

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
