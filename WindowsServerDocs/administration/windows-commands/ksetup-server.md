---
title: ksetup:Server
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e3407111-ac92-457f-aa1f-a04fe9109d59
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f370d4dede278e1facdda829503ea3793502b9e6
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59814575"
---
# <a name="ksetupserver"></a>ksetup:Server



Можно указать имя для компьютера под управлением ОС Windows, таким образом изменения с помощью **ksetup** обновит конечного компьютера. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /server <ServerName>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Имя_сервера >|Полное имя, на котором конфигурация начнут действовать, например IPops897.corp.contoso.com.</br>Если неполное полное доменное имя компьютера указано, команда завершится ошибкой.|

## <a name="remarks"></a>Примечания

Невозможно удалить имя целевого сервера; только его можно изменить на имя локального компьютера, который используется по умолчанию.

Имя целевого сервера хранится в реестре в **HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\LSA\Kerberos**. Оно не будет отмечено с помощью **ksetup**.

## <a name="BKMK_Examples"></a>Примеры

Сделать ваши **ksetup** конфигурации, действующих на компьютере IPops897, который подключен в домене Contoso:
```
ksetup /server IPops897.corp.contoso.com
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ksetup](ksetup.md)
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)