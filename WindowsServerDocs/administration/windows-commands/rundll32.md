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
ms.openlocfilehash: 29a87f9f07c25a0c671e47550e0a054d8308f747
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71384417"
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

Rundll32 может вызывать функции только из библиотеки DLL, которые явно написаны для вызова с помощью rundll32. Дополнительные сведения о требованиях rundll32 см. в [статье 164787](https://go.microsoft.com/fwlink/?LinkID=165773) базы знаний майкрософт (https://go.microsoft.com/fwlink/?LinkID=165773) ).

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)