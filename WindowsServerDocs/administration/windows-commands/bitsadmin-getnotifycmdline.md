---
title: bitsadmin getnotifycmdline
description: Раздел команд Windows для **битсадмин жетнотификмдлине**, который получает команду командной строки, которая выполняется, когда задание завершает передачу данных.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 90fa33e6-aca5-4a23-82bd-19a9f13f8416
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 24b49b3fa0c2dafb999d8cb9c6e0c13ae68bf6f4
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850597"
---
# <a name="bitsadmin-getnotifycmdline"></a>bitsadmin getnotifycmdline

Получает команду командной строки, которая будет выполнена, когда задание завершает передачу данных.

> [!NOTE]
> Эта команда не поддерживается в БИТАХ 1,2 и более ранних версиях.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getnotifycmdline <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задания | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере извлекается команда командной строки, используемая службой при завершении задания с именем *мидовнлоаджоб* .

```
C:\>bitsadmin /getnotifycmdline myDownloadJob
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)