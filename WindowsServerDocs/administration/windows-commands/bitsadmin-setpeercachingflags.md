---
title: битсадмин сетпиркачингфлагс
description: Раздел команд Windows для битсадмин сетпиркачингфлагс, который устанавливает флаги, определяющие, могут ли файлы задания кэшироваться и обслуживаться одноранговым узлам, а также может ли задание скачивать содержимое с одноранговых узлов.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3f54a127-fb68-49a5-b843-664ec833df67
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d19e4d14b47e4aa96e9ad9d4367e872350ad4d43
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849247"
---
# <a name="bitsadmin-setpeercachingflags"></a>битсадмин сетпиркачингфлагс

Устанавливает флаги, определяющие, могут ли файлы задания кэшироваться и обслуживаться одноранговым узлам, а также может ли задание скачивать содержимое с одноранговых узлов.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetPeerCachingFlags <Job> <value> 
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|
|Значение|Значением является целое число без знака со следующей интерпретацией битов в двоичном представлении.</br>1 — задание может скачивать содержимое с одноранговых узлов.</br>2 — файлы задания могут кэшироваться и обслуживаться одноранговыми узлами.|

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере задаются флаги для задания с именем *myJob* , которое позволяет загрузить содержимое с одноранговых узлов.
```
C:\>bitsadmin / SetPeerCachingFlags myJob 1 
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)