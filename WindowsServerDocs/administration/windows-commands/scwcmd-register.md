---
title: Регистрация Scwcmd
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fe4d126a-9f27-4076-b7b1-fbefa45f378a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: cc8b4a06af519b0da01dfcab8de0139b12cc68f2
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59834975"
---
# <a name="scwcmd-register"></a>Scwcmd: register

> Область применения. Windows Server 2012 R2, Windows Server 2012

Расширяет или настраивает базы данных конфигурации безопасности мастер настройки безопасности (SCW), зарегистрировав файл базы данных настройки безопасности, содержащий роли, задачи, службы или определения порта.

## <a name="syntax"></a>Синтаксис

```
scwcmd register /kbname:<MyApp> [/kbfile:<kb.xml>] [/kb:<path>] [/d]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/kbname:\<MyApp >|Указывает имя, под которым будет зарегистрирована расширение базы данных настройки безопасности. Этот параметр должен быть указан.|
|/kbfile:\<Kb.xml>|Указывает путь и имя файла базы данных конфигурации безопасности, который будет использоваться для расширения и настройки базы данных конфигурации безопасности. Чтобы проверить, что файл базы данных конфигурации безопасности совместим со схемой SCW, используйте файл определения схемы %windir%\security\KBRegistrationInfo.xsd. Необходимо указать этот параметр, если **/d** указан параметр.|
|/KB:\<путь >|Указывает путь к каталогу, содержащему файлы базы данных конфигурации безопасности SCW обновляться. Если этот параметр не указан, используется %windir%\security\msscw\kbs.|
|/d|Отменяет регистрацию расширение безопасности базы данных конфигурации из базы данных конфигурации безопасности. В параметре /kbname указано расширение, чтобы отменить регистрацию. ( **/Kbfile** параметр указывать не нужно.) Определяется базой данных конфигурации безопасности для отмены регистрации расширение из **/kb** параметра.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

Scwcmd.exe доступна только на компьютерах под управлением Windows Server 2008 R2, Windows Server 2008 или Windows Server 2003.

## <a name="BKMK_Examples"></a>Примеры

Чтобы зарегистрировать файл базы данных настройки безопасности, с именем SCWKBForMyApp.xml под именем MyApp в папке \\ \\kbserver\kb, тип:
```
scwcmd register /kbfile:d:\SCWKBForMyApp.xml /kbname:MyApp /kb:\\kbserver\kb
```
Чтобы отменить регистрацию MyApp базы данных конфигурации безопасности, расположенный \\ \\kbserver\kb, тип:
```
scwcmd register /d /kbname:MyApp /kb:\\kbserver\kb
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)