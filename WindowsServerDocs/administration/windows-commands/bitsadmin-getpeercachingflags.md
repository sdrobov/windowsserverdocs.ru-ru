---
title: битсадмин жетпиркачингфлагс
description: Раздел команд Windows для **битсадмин жетпиркачингфлагс**, который получает флаги, которые определяют, могут ли файлы задания кэшироваться и обслуживаться одноранговым узлам, а также, если служба BITS может скачивать содержимое для задания с одноранговых узлов.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3c3c9f28-4c04-4c49-a23a-dee5bbcc8981
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: cdf9683d1a65400286b4604bd9420a5ab863d4af
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850557"
---
# <a name="bitsadmin-getpeercachingflags"></a>битсадмин жетпиркачингфлагс

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Получает флаги, которые определяют, могут ли файлы задания кэшироваться и обслуживаться одноранговым узлам, а также, если служба BITS может скачивать содержимое для задания с одноранговых узлов.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getpeercachingflags <job> 
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задания | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере извлекаются флаги для задания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /getpeercachingflags myJob
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)