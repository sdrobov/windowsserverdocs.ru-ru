---
title: bitsadmin getreplydata
description: Справочная статья по команде битсадмин жетреплидата, которая получает данные отправки и ответа сервера в шестнадцатеричном формате для задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 819f97d5-b255-4b2d-9f63-0daa73915434
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 86c8a57664d6f90980212766e8e2bd2df6d95181
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926745"
---
# <a name="bitsadmin-getreplydata"></a>bitsadmin getreplydata

Получает данные отправки и ответа сервера в шестнадцатеричном формате для задания.

> [!NOTE]
> Эта команда не поддерживается в БИТАХ 1,2 и более ранних версиях.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getreplydata <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a>Примеры

Чтобы получить данные отправки и ответа для задания с именем *мидовнлоаджоб*, выполните следующие действия.

```
bitsadmin /getreplydata myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
