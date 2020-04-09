---
title: представлены
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9b0a21cf-3bef-4ade-b8f1-ac42f9203947
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 55cc7a292b81977a346f3f078a3b5623243ea46c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80844807"
---
# <a name="expose"></a>представлены



предоставляет постоянную теневую копию в виде буквы диска, общего ресурса или точки подключения.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
expose <ShadowID> {<Drive:> | <Share> | <MountPoint>}
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|шадовид|Указывает теневой идентификатор теневой копии, которую необходимо предоставить.|
|\<диск: >|Предоставляет указанную теневую копию в виде буквы диска (например, P:).|
|\<общий доступ >|Предоставляет указанную теневую копию в общей папке (например, \\\\*MachineName*\).|
|\<точка подключения >|Предоставляет указанную теневую копию точке подключения (например, К:\шадовкопи\).|

## <a name="remarks"></a>Примечания

-   Вместо *шадовид*можно использовать существующий псевдоним или переменную среды. Чтобы просмотреть существующие псевдонимы, используйте параметр **Добавить** без параметров.

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы предоставить устойчивую теневую копию, связанную с переменной среды VSS_SHADOW_1, в качестве диска X, введите:
```
expose %vss_shadow_1% x:
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)