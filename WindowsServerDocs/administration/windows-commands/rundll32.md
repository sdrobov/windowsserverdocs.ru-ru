---
title: rundll32
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 46d9cd64-8186-4cd4-a500-44700340fe81
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b0639206b26ea58c4ec8473c0a736fda3c435021
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82722236"
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

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
