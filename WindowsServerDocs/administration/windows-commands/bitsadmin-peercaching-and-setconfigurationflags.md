---
title: битсадмин (кэшированный) и сетконфигуратионфлагс
description: Команды Windows для **битсадмин кэшированных** данных и **сетконфигуратионфлагс**, которые устанавливают флаги конфигурации, определяющие, может ли компьютер передавать содержимое одноранговым узлам, а также может ли он скачивать содержимое с одноранговых узлов.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ff0a2b49-66e3-4d40-824c-6a3816055d2e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ebaa09da2d4594d2762e67dc5884dd15cf4d1da8
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850137"
---
# <a name="bitsadmin-peercaching-and-setconfigurationflags"></a>битсадмин (кэшированный) и сетконфигуратионфлагс

Задает флаги конфигурации, которые определяют, может ли компьютер передавать содержимое одноранговым узлам, а также может ли он скачивать содержимое с одноранговых узлов.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /peercaching /setconfigurationflags <job> <value>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задания | Отображаемое имя задания или идентификатор GUID. |
| value | Целое число без знака со следующей интерпретацией битов в двоичном представлении:<ul><li> Чтобы разрешить загрузку данных задания с однорангового узла, установите наименьший значащий бит.</li><li>Чтобы разрешить передачу данных задания одноранговым узлам, установите второй бит справа.</li></ul>|

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере указываются данные задания, которые должны быть загружены с одноранговых узлов для задания с именем *мидовнлоаджоб*.

```
C:\> bitsadmin /peercaching /setconfigurationflags myDownloadJob 1
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)