---
title: ksetup server
description: Справочная статья по команде сервера ksetup, которая позволяет указать имя компьютера под управлением операционной системы Windows, поэтому изменения, внесенные командой ksetup, обновляют конечный компьютер.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e3407111-ac92-457f-aa1f-a04fe9109d59
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 99c708c3842d1d2d36783db09d60750bb2703670
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926099"
---
# <a name="ksetup-server"></a>ksetup server

Позволяет указать имя компьютера под управлением операционной системы Windows, поэтому изменения, внесенные командой **ksetup** , обновляют целевой компьютер.

Имя целевого сервера хранится в реестре в разделе `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\LSA\Kerberos` . Эта запись не отображается при выполнении команды **ksetup** .

> [!IMPORTANT]
> Удалить имя целевого сервера невозможно. Вместо этого можно вернуться к локальному имени компьютера, используемому по умолчанию.

## <a name="syntax"></a>Синтаксис

```
ksetup /server <servername>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<servername>` | Указывает полное имя компьютера, на котором будет действовать конфигурация, например *IPops897.Corp.contoso.com*.<p>Если указано неполное полное доменное имя компьютера, команда завершится ошибкой. |

### <a name="examples"></a>Примеры

Чтобы обеспечить эффективную настройку **ksetup** на компьютере *IPops897* , подключенном к домену contoso, введите:

```
ksetup /server IPops897.corp.contoso.com
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда ksetup](ksetup.md)
