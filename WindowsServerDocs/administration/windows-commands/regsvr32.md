---
title: regsvr32
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 444af0ccf7c9bbe21c013f32b396997b7cb2e00f
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71371633"
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
|/u|Отменяет регистрацию сервера.|
|/s|Запускает **regsvr32** без отображения сообщений.|
|параметра|Запускает **regsvr32** без вызова функции **DllRegisterServer**. (Требуется параметр **/i** .)|
|/i:\<cmdline >|Передает необязательную строку командной строки (*cmdline*) в **DllInstall**. Если этот параметр используется вместе с параметром **/u** , он вызывает **дллунинсталл**.|
|\<DllName >|Имя DLL-файла, который будет зарегистрирован.|
|/?|Отображение справки в командной строке.|

## <a name="BKMK_examples"></a>Примеров

Чтобы зарегистрировать библиотеку. dll для схемы Active Directory, введите:
```
regsvr32 schmmgmt.dll
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)