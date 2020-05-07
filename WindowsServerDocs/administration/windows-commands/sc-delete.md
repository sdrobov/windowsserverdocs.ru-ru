---
title: SC. exe Delete
description: Узнайте, как отменить регистрацию служб с помощью служебной программы SC. exe
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2fe94fb3-e4d1-47b5-b999-39995ecbb644
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 284012cf6799df52832e62c3eea1b2f0fcd84805
ms.sourcegitcommit: 95b60384b0b070263465eaffb27b8e3bb052a4de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2020
ms.locfileid: "82850115"
---
# <a name="scexe-delete"></a>SC. exe Delete

Удаляет подраздел службы из реестра. Если служба запущена или другой процесс имеет открытый обработчик, служба помечается для удаления.

В разделе [Примеры](#examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
sc.exe [<ServerName>] delete [<ServiceName>]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Имя сервера>|Указывает имя удаленного сервера, на котором расположена служба. Имя должно использовать формат UNC (например, \\ \\MyServer). Чтобы запустить SC. exe локально, опустите этот параметр.|
|\<> ServiceName|Указывает имя службы, возвращенное операцией **жеткэйнаме** .|
|?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

Не рекомендуется использовать SC. exe для удаления встроенных служб операционной системы, таких как DHCP, DNS или службы IIS. Сведения об установке, удалении и перенастройке ролей операционной системы, служб и компонентов см. в разделе [Установка и удаление ролей, служб ролей или компонентов](/WindowsServerDocs/administration/server-manager/install-or-uninstall-roles-role-services-or-features.md) .

## <a name="examples"></a>Примеры

Чтобы удалить подраздел Service **невсерв** из реестра на локальном компьютере, введите:
```
sc.exe delete newserv
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
