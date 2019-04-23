---
title: rundll32
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 5b1f288d21a1dcac25ecc00f685ea179d8a6542f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59835035"
---
# <a name="rundll32"></a>rundll32



Загружает и выполняет 32-разрядной библиотеки динамической компоновки (DLL). Не предусмотрены настраиваемые параметры для Rundll32. Справочная информация предоставляется в конкретной библиотеке DLL, с помощью **rundll32** команды.

Необходимо запустить **rundll32** команду из командной строки с повышенными правами. Чтобы открыть командную строку с повышенными правами, нажмите кнопку **запустить**, щелкните правой кнопкой мыши **командной строки**, а затем нажмите кнопку **Запуск от имени администратора**.

## <a name="syntax"></a>Синтаксис

```
Rundll32 <DLLname>
```

## <a name="commands"></a>Команды

|Параметр|Описание|
|---------|-----------|
|[Rundll32 printui.dll,PrintUIEntry](rundll32-printui.md)|Отображает интерфейс пользователя принтера|

## <a name="remarks"></a>Примечания

Rundll32 может вызывать только функции из библиотеки DLL, написанные явным образом вызывать Rundll32. Дополнительные сведения о Rundll32 требования см. в разделе [статьи 164787](https://go.microsoft.com/fwlink/?LinkID=165773) в базе знаний Майкрософт (https://go.microsoft.com/fwlink/?LinkID=165773).

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)