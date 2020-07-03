---
title: Update-Серверфилес
description: Справочная статья по Update-Серверфилес, которая обновляет файлы в общей папке REMINST с использованием последних файлов, которые хранятся в папке%Windir%\System32\RemInst сервера.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 23aa79df-38c6-401e-91bd-cd23811b30b4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 79b9332d5962c7e3c50ea3d7c71f33111a0e74b8
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85930130"
---
# <a name="update-serverfiles"></a>Update-Серверфилес

Обновляет файлы в общей папке REMINST с помощью последних файлов, которые хранятся в папке%Windir%\System32\RemInst сервера. Чтобы обеспечить допустимость установки служб развертывания Windows, эту команду следует выполнять один раз после каждого обновления сервера, установки пакета обновления или обновления файлов служб развертывания Windows.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL [Options] /Update-ServerFiles [/Server:<Server name>]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[/Server: \<Server name> ]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|

## <a name="examples"></a>Примеры

Чтобы обновить файлы, введите одно из следующих действий.
```
WDSUTIL /Update-ServerFiles
WDSUTIL /Verbose /Progress /Update-ServerFiles /Server:MyWDSServer
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)