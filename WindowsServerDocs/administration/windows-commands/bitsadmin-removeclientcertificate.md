---
title: битсадмин ремовеклиентцертификате
description: Раздел команд Windows для **битсадмин ремовеклиентцертификате**, который удаляет сертификат клиента из задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b417c3e5-aadd-4fcc-968f-45d8b67ca516
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 312226b73b91385436e15c4afbb49df161258768
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81123106"
---
# <a name="bitsadmin-removeclientcertificate"></a>битсадмин ремовеклиентцертификате

Удаляет сертификат клиента из задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /removeclientcertificate <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задания | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a>Примеры

В следующем примере удаляется сертификат клиента из задания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /removeclientcertificate myDownloadJob 
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)