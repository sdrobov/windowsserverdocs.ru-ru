---
title: rundll32
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 46d9cd64-8186-4cd4-a500-44700340fe81
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7345c1ad59a4209e607245db1b2a79055ffcb5fe
ms.sourcegitcommit: 1c75e4b3f5895f9fa33efffd06822dca301d4835
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77517290"
---
# <a name="rundll32"></a>rundll32



Загружает и выполняет 32-разрядные библиотеки динамической компоновки (DLL). Настраиваемые параметры для rundll32 отсутствуют. Справочные сведения предоставляются для конкретной библиотеки DLL, выполняемой с помощью команды **rundll32** .

Необходимо выполнить команду **rundll32** из командной строки с повышенными привилегиями. Чтобы открыть командную строку с повышенными привилегиями, нажмите кнопку **Пуск**, щелкните правой кнопкой мыши пункт **Командная строка**и выберите команду **Запуск от имени администратора**.

## <a name="syntax"></a>Синтаксис

```
Rundll32 <DLLname>
```

## <a name="commands"></a>Команды

|Параметр|Описание|
|---------|-----------|
|[Rundll32 PRINTUI. dll, Принтуиентри](rundll32-printui.md)|Отображает пользовательский интерфейс принтера|

## <a name="remarks"></a>Примечания

Rundll32 может вызывать только функции из библиотеки DLL, которые были явно написаны для вызова с помощью rundll32.

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
