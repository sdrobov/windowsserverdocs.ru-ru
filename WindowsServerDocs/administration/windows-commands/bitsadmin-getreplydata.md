---
title: bitsadmin getreplydata
description: Справочный раздел по команде битсадмин жетреплидата, который получает данные о передаче и ответах сервера в шестнадцатеричном формате для задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 819f97d5-b255-4b2d-9f63-0daa73915434
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ea2a82403fe05776abbbf65e87a4b6e72c8767b8
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717626"
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
