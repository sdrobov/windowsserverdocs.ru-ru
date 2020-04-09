---
title: regsvr32
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3345e964-7d3e-42b8-abeb-42ed6edfe2b2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d3b775b0c49e4191a9fee6dc9e2e91f968142085
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80836217"
---
# <a name="regsvr32"></a>regsvr32



Регистрирует DLL-файлы в качестве компонентов команды в реестре.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
regsvr32 [/u] [/s] [/n] [/i[:cmdline]] <DllName>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/u|Отменяет регистрацию сервера.|
|/s|Запускает **regsvr32** без отображения сообщений.|
|/n|Запускает **regsvr32** без вызова функции **DllRegisterServer**. (Требуется параметр **/i** .)|
|/i:\<cmdline >|Передает необязательную строку командной строки (*cmdline*) в **DllInstall**. Если этот параметр используется вместе с параметром **/u** , он вызывает **дллунинсталл**.|
|\<DllName >|Имя DLL-файла, который будет зарегистрирован.|
|/?|Отображает справку в командной строке.|

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы зарегистрировать библиотеку. dll для схемы Active Directory, введите:
```
regsvr32 schmmgmt.dll
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)