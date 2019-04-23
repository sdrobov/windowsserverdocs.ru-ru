---
title: regsvr32
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3345e964-7d3e-42b8-abeb-42ed6edfe2b2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 87d9291755ddb4484e85248cb01ad78b01a25965
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59889995"
---
# <a name="regsvr32"></a>regsvr32



Регистрирует DLL-файлы в качестве компонентов команды в реестре.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
regsvr32 [/u] [/s] [/n] [/i[:cmdline]] <DllName>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/u|Отмена регистрации сервера.|
|/s|Запуски **Regsvr32** без отображения сообщения.|
|/n|Запуски **Regsvr32** без вызова **DllRegisterServer**. (Требуется **/i** параметр.)|
|/i:\<cmdline>|Передает необязательная строка командной строки (*cmdline*) для **DllInstall**. Если этот параметр используется в сочетании с **/u** параметр, он вызывает **DllUninstall**.|
|\<DllName >|Имя DLL-файла, которое будет зарегистрировано.|
|/?|Отображение справки в командной строке.|

## <a name="BKMK_examples"></a>Примеры

Чтобы зарегистрировать DLL-файл для схемы Active Directory, введите следующую команду:
```
regsvr32 schmmgmt.dll
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)