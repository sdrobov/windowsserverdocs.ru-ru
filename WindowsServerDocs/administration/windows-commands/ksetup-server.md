---
title: сервер ksetup
description: Справочный раздел по команде сервера ksetup, который позволяет указать имя компьютера под управлением операционной системы Windows, поэтому изменения, внесенные командой ksetup, обновляют конечный компьютер.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e3407111-ac92-457f-aa1f-a04fe9109d59
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e39a3fbef4b99848d2a90c81007c526597c77275
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83817524"
---
# <a name="ksetup-server"></a>сервер ksetup

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
