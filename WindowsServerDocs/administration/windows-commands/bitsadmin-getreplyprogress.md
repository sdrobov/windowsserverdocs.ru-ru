---
title: bitsadmin getreplyprogress
description: Раздел команд Windows для **битсадмин жетреплипрогресс**, который извлекает размер и ход отправки ответа сервера.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7f7cb0b4-ad95-44fd-a35d-0ddf5fc0b0d0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 195ed669817bc0aca7ebc432e7f3c66ab1548162
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850487"
---
# <a name="bitsadmin-getreplyprogress"></a>bitsadmin getreplyprogress

Возвращает размер и ход ответа отправки сервера.

> [!NOTE]
> Эта команда не поддерживается в БИТАХ 1,2 и более ранних версиях.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getreplyprogress <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задания | Отображаемое имя задания или идентификатор GUID. |


## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере извлекается ход выполнения отправки ответа для задания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /getreplyprogress myDownloadJob
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)