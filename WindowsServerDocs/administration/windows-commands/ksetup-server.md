---
title: 'ksetup: сервер'
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e3407111-ac92-457f-aa1f-a04fe9109d59
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7889e1a03d3c0eec1958bf1d6356c67e9371a80f
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841447"
---
# <a name="ksetupserver"></a>ksetup: сервер



Позволяет указать имя компьютера под управлением операционной системы Windows, чтобы изменения, вносимые с помощью **ksetup** , приводят к обновлению целевого компьютера. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /server <ServerName>
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<ServerName >|Полное имя компьютера, на котором будет действовать конфигурация, например IPops897.corp.contoso.com.</br>Если указано неполное полное доменное имя компьютера, команда завершится ошибкой.|

## <a name="remarks"></a>Примечания

Удалить имя целевого сервера невозможно. Вы можете изменить его обратно на локальное имя компьютера, которое является значением по умолчанию.

Имя целевого сервера хранится в реестре в **HKEY_LOCAL_MACHINE \system\controlset001\control\lsa\kerberos**. Он не сообщается с помощью **ksetup**.

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров

Сделайте конфигурацию **ksetup** эффективной на компьютере IPops897, подключенном к домену contoso:
```
ksetup /server IPops897.corp.contoso.com
```

## <a name="additional-references"></a>Дополнительные материалы

-   [Ksetup](ksetup.md)
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)