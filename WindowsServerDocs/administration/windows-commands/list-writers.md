---
title: модули записи списка
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1c30cbc4-f568-4fa7-b564-66c41d3ca82d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1e12c4f36c3fd840b7b37b12d9f4171429e5a52d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841117"
---
# <a name="list-writers"></a>модули записи списка



Выводит список модулей записи, наявляющихся в системе. Если используется без параметров, в **списке** отображаются выходные данные для **метаданных списка** по умолчанию.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
list writers [metadata | detailed | status]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|метаданные|Перечисляет удостоверение и состояние модулей записи, а также отображает метаданные, такие как сведения о компонентах и исключенные файлы. Это параметр по умолчанию.|
|подробные сведения|Выводит те же сведения, что и **метаданные**, но **подробно** включает полный список файлов для всех компонентов.|
|состояние|Выводит только удостоверение и состояние зарегистрированных модулей записи.|

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы вывести только удостоверение и состояние модулей записи, введите:
```
list writers status
```
Выходные данные, аналогичные показанным ниже.
```
Listing writer status ...
* WRITER System Writer
        - Status: 5 (VSS_WS_WAITING_FOR_BACKUP_COMPLETE)
        - Writer Failure code: 0x00000000 (S_OK)
        - Writer ID: {e8132975-6f93-4464-a53e-1050253ae220}
        - Instance ID: {7e631031-c695-4229-9da1-a7de057e64cb}
* WRITER Shadow Copy Optimization Writer
        - Status: 1 (VSS_WS_STABLE)
        - Writer Failure code: 0x00000000 (S_OK)
        - Writer ID: {4dc3bdd4-ab48-4d07-adb0-3bee2926fd7f}
        - Instance ID: {9e362607-9794-4dd4-a7cd-b3d5de0aad20}
...
...
...
* WRITER Registry Writer
        - Status: 1 (VSS_WS_STABLE)
        - Writer Failure code: 0x00000000 (S_OK)
        - Writer ID: {afbab4a2-367d-4d15-a586-71dbb18f8485}
        - Instance ID: {e87ba7e3-f8d8-42d8-b2ee-c76ae26b98e8}
8 writers listed. 
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)