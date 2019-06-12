---
title: С помощью команды get-AllServers
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fe2e3c69-8f2e-457d-af55-d249ebf70f53
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: dbccb834f9058f2c3cca097cdf998455f2a6892e
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66440493"
---
# <a name="using-the-get-allservers-command"></a>С помощью команды get-AllServers



Извлекает сведения обо всех серверах службы развертывания Windows.

> [!NOTE]
> Эта команда может занять продолжительное время выполнения, если имеется много серверов служб развертывания Windows в вашей среде или используется медленное подключение сети, связанные серверы.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL [Options] /Get-AllServers /Show:{Config | Images | All} [/Detailed] [/Forest:{Yes | No}]
```

## <a name="parameters"></a>Параметры

|   Параметр   |                                                                                                                 Описание                                                                                                                  |
|---------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| / Показать: {Config |                                                                                                                    Изображений                                                                                                                    |
|  [/ Подробные]  | При использовании в сочетании с **/Show:Images** или **/Show:All**, возвращает все изображений метаданные из каждого изображения. Если **/подробные** параметр не указан, по умолчанию задается для возврата имени образа, описание и имя файла. |
| [/ Леса: {Да |                                                                                                                     No}]                                                                                                                     |

## <a name="BKMK_examples"></a>Примеры

Чтобы просмотреть сведения обо всех серверах, введите следующую команду:
```
WDSUTIL /Get-AllServers /Show:Config
```
Чтобы просмотреть подробные сведения обо всех серверах, введите:
```
WDSUTIL /Verbose /Get-AllServers /Show:All /Detailed /Forest:Yes
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)