---
title: bitsadmin removeclientcertificate
description: Справочная статья по команде битсадмин ремовеклиентцертификате, которая удаляет сертификат клиента из задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b417c3e5-aadd-4fcc-968f-45d8b67ca516
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3659f830b9462469762fcd4c7690295073400b1e
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927986"
---
# <a name="bitsadmin-removeclientcertificate"></a>bitsadmin removeclientcertificate

Удаляет сертификат клиента из задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /removeclientcertificate <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a>Примеры

Чтобы удалить сертификат клиента из задания с именем *мидовнлоаджоб*, выполните следующие действия.

```
bitsadmin /removeclientcertificate myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
