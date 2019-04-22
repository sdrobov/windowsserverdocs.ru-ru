---
title: bitsadmin setproxysettings
description: Раздел Windows команды для **bitsadmin setproxysettings** -задает параметры прокси-сервера для указанного задания.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: be8edb1b-614e-4d0b-a8f8-64b4bde3e64b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a3503aab55f5650cb9283ce8a9f1a17359bfd48b
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59825595"
---
# <a name="bitsadmin-setproxysettings"></a>bitsadmin setproxysettings



Задает параметры прокси-сервера для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetProxySettings <Job> <Usage> [List] [Bypass]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|
|Использование|Принимает одно из следующих значений:</br>-PRECONFIG — использовать значения по умолчанию Internet Explorer владельца.</br>-NO_PROXY — не использовать прокси-сервер.</br>— ПЕРЕОПРЕДЕЛЕНИЕ — использовать список явных прокси-сервера, а также в список исключений. Прокси-сервера и список обхода прокси-сервера необходимо выполнить.</br>-АВТООБНАРУЖЕНИЕ — автоматическое определение параметров прокси-сервера.|
|List|Используется, когда *использования* параметр имеет значение ПЕРЕОПРЕДЕЛЕНИЯ — содержит список прокси-серверы для использования с разделителями запятыми.|
|Обход проверки|Используется, когда *использования* параметр имеет значение ПЕРЕОПРЕДЕЛЕНИЯ — содержит список с разделителями пробелами имена узлов или IP-адреса или оба параметра, для которого передачи которых не должны направляться через прокси-сервер. Это может быть  **\<локальный >** для ссылки на все серверы в той же локальной сети. Значение NULL или «» может использоваться для обхода списка пустой прокси-сервера.|

## <a name="BKMK_examples"></a>Примеры

В следующем примере задается параметры прокси-сервера для задания с именем *myDownloadJob*.

```
C:\>bitsadmin /SetProxySettings myDownloadJob PRECONFIG
```

Ниже приведены некоторые другие примеры.

```
bitsadmin /setproxysettings myDownloadJob NO_PROXY
bitsadmin /setproxysettings myDownloadJob OVERRIDE proxy1:80 ""
bitsadmin /setproxysettings myDownloadJob OVERRIDE proxy1,proxy2,proxy3 NULL
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)