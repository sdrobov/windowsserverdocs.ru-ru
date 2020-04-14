---
title: битсадмин (кэшированный) и жетконфигуратионфлагс
description: Команды Windows для **битсадмин кэширования** и **жетконфигуратионфлагс**, которые получают флаги конфигурации, которые определяют, обслуживает ли компьютер содержимое одноранговым узлам, и может ли он скачивать содержимое с одноранговых узлов.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 124ddc15-3444-4bd5-96e5-c6bfabe4f9c2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: be8d6a719d63c8e9c6250320560b6ce21274c680
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850177"
---
# <a name="bitsadmin-peercaching-and-getconfigurationflags"></a>битсадмин (кэшированный) и жетконфигуратионфлагс

Получает флаги конфигурации, которые определяют, обслуживает ли компьютер содержимое одноранговым узлам, и может ли он скачивать содержимое с одноранговых узлов.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /peercaching /getconfigurationflags <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задания | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере показано получение флагов конфигурации для задания с именем *мидовнлоаджоб*.

```
C:\> bitsadmin /peercaching /getconfigurationflags myDownloadJob
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)