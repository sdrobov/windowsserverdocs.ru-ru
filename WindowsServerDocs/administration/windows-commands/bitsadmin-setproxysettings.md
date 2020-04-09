---
title: bitsadmin setproxysettings
description: Раздел команд Windows для битсадмин setproxysettings, который задает параметры прокси-сервера для указанного задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: be8edb1b-614e-4d0b-a8f8-64b4bde3e64b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4dea72d956d12070b2638f953a7a00dcb1ed7a9c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849207"
---
# <a name="bitsadmin-setproxysettings"></a>bitsadmin setproxysettings

Задает параметры прокси-сервера для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetProxySettings <Job> <Usage> [List] [Bypass]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|
|Использование|Принимает одно из следующих значений:</br>— Предварительная настройка — используйте значения по умолчанию для свойства Owner в Internet Explorer.</br>-NO_PROXY — не использовать прокси-сервер.</br>-OVERRIDE — Используйте явный список прокси-серверов и список обхода. Должен следовать список обхода прокси-сервера и прокси-сервера.</br>— Автообнаружение — автоматическое определение параметров прокси-сервера.|
|List|Используется, если параметр *использования* имеет значение override, содержит разделенный запятыми список прокси-серверов для использования.|
|Пустите|Используется, если параметр *использования* имеет значение переопределение, содержит разделенный пробелами список имен узлов или IP-адресов, для которых передачи не направляются через прокси-сервер. Это может быть **\<локальным >** для ссылки на все серверы в одной локальной сети. Значения NULL или могут использоваться для пустого списка обхода прокси-сервера.|

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере задаются параметры прокси-сервера для задания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /SetProxySettings myDownloadJob PRECONFIG
```

Ниже приведены некоторые другие примеры.

```
bitsadmin /setproxysettings myDownloadJob NO_PROXY
bitsadmin /setproxysettings myDownloadJob OVERRIDE proxy1:80 
bitsadmin /setproxysettings myDownloadJob OVERRIDE proxy1,proxy2,proxy3 NULL
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)