---
title: msdt
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ead1b672-a120-4e16-94aa-a8e13602c1d0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 781e83615d44a4adb20fd85fe5ce6ebc7c2d4966
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59818835"
---
# <a name="msdt"></a>msdt



Вызывает по устранению неполадок пакета, в командной строке или как часть автоматизированного скрипта и предоставляет дополнительные параметры без участия пользователя.

## <a name="syntax"></a>Синтаксис

```
msdt </id <name> | /path <name> | /cab < name>> <</parameter> [options] … <parameter> [options]>>
```

## <a name="parameters"></a>Параметры

В следующей таблице содержатся параметры и параметры, поддерживаемые msdt.exe.

|Параметр|Описание|
|---------|-----------|
|/ID \<имя пакета >|Указывает, какой пакет диагностики, для запуска. Список доступных пакетов см. в разделе Устранение неполадок ИД пакета в разделе «доступны диагностические пакеты? подразделе данного раздела.|
|/ Path \<каталога | файл .diagpkg | файл .diagcfg >|Указывает полный путь к пакету диагностики. Если необходимо указать каталог, каталог должен содержать диагностического пакета. Параметр/Path нельзя использовать в сочетании с */id*, */dci*, или */cab* параметра.|
|/dci \<passkey>|Заполняет поле ключ доступа в технической поддержки от Майкрософт. Этот параметр используется только в том случае, если поставщику услуг технической поддержки предоставил ключ доступа.|
|/dt \<directory>|Отображает журнал по устранению неполадок в указанном каталоге. Результаты диагностики, хранятся в пользователя **%LOCALAPPDATA%\Diagnostics** или **%LOCALAPPDATA%\ElevatedDiagnostics** каталоги.|
|/AF \<файл ответов >|Указывает файл ответов в формате XML, содержащий ответы на один или несколько диагностических взаимодействия.|
