---
title: кэш битсадмин и делетеурл
description: Раздел команд Windows для **кэша битсадмин и делетеурл**, удаляющий все записи кэша для данного URL-адреса.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e108b76b-fae9-4c16-bf4c-d74c9f025953
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 70099e795d0f05d0fcf75fbf6b82f5466d1c0c55
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850937"
---
# <a name="bitsadmin-cache-and-deleteurl"></a>кэш битсадмин и делетеурл

Удаляет все записи кэша для заданного URL-адреса.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /deleteURL url
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| url | Универсальный указатель ресурсов, определяющий удаленный файл. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере удаляются все записи кэша для `https://www.contoso.com/en/us/default.aspx`

```
C:\>bitsadmin /deleteURL https://www.contoso.com/en/us/default.aspx 
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)