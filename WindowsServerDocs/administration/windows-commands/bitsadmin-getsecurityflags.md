---
title: битсадмин жетсекуритифлагс
description: Раздел команд Windows для **битсадмин жетсекуритифлагс**, который сообщает флаги безопасности HTTP для перенаправления URL-адресов и проверки, выполняемые на сертификате сервера во время перемещения.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c2e73519-34f4-487b-af11-97d5d08ef9bb
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 360f8d5514e5251dd9e4a6a6b60335dc34fe4415
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850477"
---
# <a name="bitsadmin-getsecurityflags"></a>битсадмин жетсекуритифлагс

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Сообщает о флагах безопасности HTTP для перенаправления URL-адресов и проверках, выполняемых на сертификате сервера во время перемещения.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getsecurityflags <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задания | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере извлекаются флаги безопасности из задания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /getsecurityflags myDownloadJob
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)