---
title: bitsadmin setproxysettings
description: Раздел команд Windows для **битсадмин setproxysettings** — задает параметры прокси-сервера для указанного задания.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 38987c88bcfc93ea9251583b7914f982cf79e057
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380471"
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
|Job|Отображаемое имя задания или идентификатор GUID|
|Использование|Принимает одно из следующих значений:</br>— Предварительная настройка — используйте значения по умолчанию для свойства Owner в Internet Explorer.</br>-NO_PROXY — не использовать прокси-сервер.</br>-OVERRIDE — Используйте явный список прокси-серверов и список обхода. Должен следовать список обхода прокси-сервера и прокси-сервера.</br>— Автообнаружение — автоматическое определение параметров прокси-сервера.|
|List|Используется, если параметр *использования* имеет значение override, содержит разделенный запятыми список прокси-серверов для использования.|
|Пустите|Используется, если параметр *использования* имеет значение переопределение, содержит разделенный пробелами список имен узлов или IP-адресов, для которых передачи не направляются через прокси-сервер. Это может быть **\<local >** для ссылки на все серверы в одной локальной сети. Для пустого списка обхода прокси-сервера могут использоваться значения NULL или "".|

## <a name="BKMK_examples"></a>Примеров

В следующем примере задаются параметры прокси-сервера для задания с именем *мидовнлоаджоб*.

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

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)