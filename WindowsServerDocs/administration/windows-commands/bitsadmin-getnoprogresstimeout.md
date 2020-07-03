---
title: bitsadmin getnoprogresstimeout
description: Справочная статья по команде битсадмин жетнопрогресстимеаут, которая получает время в секундах, в течение которого служба будет пытаться переместить файл после временной ошибки.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9cd9b19b-cbb4-4352-8419-978080f016b6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 95884f5e6b0dc7ae01575ddf0cc12afea6d212c3
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927009"
---
# <a name="bitsadmin-getnoprogresstimeout"></a>bitsadmin getnoprogresstimeout

Возвращает продолжительность времени в секундах, в течение которого служба будет пытаться переместить файл после возникновения временной ошибки.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getnoprogresstimeout <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a>Примеры

Чтобы получить значение времени ожидания выполнения для задания с именем *мидовнлоаджоб*:

```
bitsadmin /getnoprogresstimeout myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
