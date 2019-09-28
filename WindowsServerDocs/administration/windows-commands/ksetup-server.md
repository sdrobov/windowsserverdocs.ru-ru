---
title: 'ksetup: сервер'
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: dd05fd294640c63e633b7b866307197ae6770476
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71374960"
---
# <a name="ksetupserver"></a>ksetup: сервер



Позволяет указать имя компьютера под управлением операционной системы Windows, чтобы изменения, вносимые с помощью **ksetup** , приводят к обновлению целевого компьютера. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /server <ServerName>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|@no__t 0ServerName >|Полное имя компьютера, на котором будет действовать конфигурация, например IPops897.corp.contoso.com.</br>Если указано неполное полное доменное имя компьютера, команда завершится ошибкой.|

## <a name="remarks"></a>Примечания

Удалить имя целевого сервера невозможно. Вы можете изменить его обратно на локальное имя компьютера, которое является значением по умолчанию.

Имя целевого сервера хранится в реестре в **HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\LSA\Kerberos**. Он не сообщается с помощью **ksetup**.

## <a name="BKMK_Examples"></a>Примеров

Сделайте конфигурацию **ksetup** эффективной на компьютере IPops897, подключенном к домену contoso:
```
ksetup /server IPops897.corp.contoso.com
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ksetup](ksetup.md)
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)