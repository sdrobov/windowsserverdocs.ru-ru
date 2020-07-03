---
title: bitsadmin getsecurityflags
description: Справочная статья по команде битсадмин жетсекуритифлагс, которая сообщает о флагах безопасности HTTP для перенаправления URL-адресов и проверках, выполняемых на сертификате сервера во время перемещения.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c2e73519-34f4-487b-af11-97d5d08ef9bb
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8613f2bd293bdbf7680aa730ec6fc222ffcfe158
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926682"
---
# <a name="bitsadmin-getsecurityflags"></a>bitsadmin getsecurityflags

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Сообщает о флагах безопасности HTTP для перенаправления URL-адресов и проверках, выполняемых на сертификате сервера во время перемещения.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getsecurityflags <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a>Примеры

Чтобы получить флаги безопасности из задания с именем *мидовнлоаджоб*, выполните следующие действия.

```
bitsadmin /getsecurityflags myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
