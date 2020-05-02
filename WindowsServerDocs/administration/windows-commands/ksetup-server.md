---
title: 'ksetup: сервер'
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e3407111-ac92-457f-aa1f-a04fe9109d59
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 91549eb78f825264016ec0e03b7035f79132f260
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724595"
---
# <a name="ksetupserver"></a>ksetup: сервер



Позволяет указать имя компьютера под управлением операционной системы Windows, чтобы изменения, вносимые с помощью **ksetup** , приводят к обновлению целевого компьютера.

## <a name="syntax"></a>Синтаксис

```
ksetup /server <ServerName>
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Имя сервера>|Полное имя компьютера, на котором будет действовать конфигурация, например IPops897.corp.contoso.com.</br>Если указано неполное полное доменное имя компьютера, команда завершится ошибкой.|

## <a name="remarks"></a>Примечания

Удалить имя целевого сервера невозможно. Вы можете изменить его обратно на локальное имя компьютера, которое является значением по умолчанию.

Имя целевого сервера хранится в реестре в **HKEY_LOCAL_MACHINE \system\controlset001\control\lsa\kerberos**. Он не сообщается с помощью **ksetup**.

## <a name="examples"></a>Примеры

Сделайте конфигурацию **ksetup** эффективной на компьютере IPops897, подключенном к домену contoso:
```
ksetup /server IPops897.corp.contoso.com
```

## <a name="additional-references"></a>Дополнительные ссылки

-   [Ksetup](ksetup.md)
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)