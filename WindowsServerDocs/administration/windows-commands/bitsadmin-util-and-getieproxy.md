---
title: bitsadmin util и getieproxy
description: Раздел Windows команды для **bitsadmin util и getieproxy** -извлекает использование прокси-сервера для учетной записи данной службы.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6d50c7e3-f4eb-4ca5-9f0c-4ed396087db6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: de4f86340b1163c4d8e3286d9c86c9df794a21c5
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59876875"
---
# <a name="bitsadmin-util-and-getieproxy"></a>bitsadmin util и getieproxy

> Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Извлекает использование прокси-сервера для учетной записи данной службы.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /Util /GetIEProxy <Account> [/Conn <ConnectionName>]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------|--------|
|Учетная запись|Учетная запись службы прокси-сервера, параметры которого требуется извлечь. Возможные значения:<br /><br />-LOCALSYSTEM<br />-СЕТЕВОЙ СЛУЖБЫ<br />-LOCALSERVICE|
|ConnectionName|Необязательно использовать с **/Conn** параметр, чтобы указать соединение для использования. Если вы не укажете **/Conn** параметр, BITS использует подключение по локальной сети. Укажите имя подключения модем сразу после **/Conn** параметра.|

## <a name="remarks"></a>Примечания

Этот параметр показывает значение для каждого использование прокси-сервера не только использование прокси-сервера вы указали для учетной записи службы. Дополнительные сведения о настройке использование прокси-сервера для учетных записей служб см. в разделе [bitsadmin util и setieproxy](bitsadmin-util-and-setieproxy.md) переключения.

## <a name="BKMK_examples"></a>Примеры

В следующем примере отображается использование прокси-сервера для учетной записи СЕТЕВОЙ службы.

```
C:\>bitsadmin /Util /GetIEProxy NETWORKSERVICE
```

## <a name="additional-references"></a>Дополнительные ссылки

[Ключ синтаксиса командной строки](command-line-syntax-key.md)
