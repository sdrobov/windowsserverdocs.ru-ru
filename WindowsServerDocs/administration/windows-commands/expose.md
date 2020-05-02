---
title: представлены
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9b0a21cf-3bef-4ade-b8f1-ac42f9203947
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 500dc5cfcd5e2bba4cfbc3cb5ef81a9065ea53cf
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725669"
---
# <a name="expose"></a>представлены



Предоставляет постоянную теневую копию в виде буквы диска, общего ресурса или точки подключения.



## <a name="syntax"></a>Синтаксис

```
expose <ShadowID> {<Drive:> | <Share> | <MountPoint>}
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|шадовид|Указывает теневой идентификатор теневой копии, которую необходимо предоставить.|
|\<Диск: >|Предоставляет указанную теневую копию в виде буквы диска (например, P:).|
|\<Общий доступ>|Предоставляет указанную теневую копию в общей папке (например, \\ \\ *MachineName*\)).|
|\<> MountPoint|Предоставляет указанную теневую копию точке подключения (например, К:\шадовкопи\).|

## <a name="remarks"></a>Примечания

-   Вместо *шадовид*можно использовать существующий псевдоним или переменную среды. Чтобы просмотреть существующие псевдонимы, используйте параметр **Добавить** без параметров.

## <a name="examples"></a>Примеры

Чтобы предоставить устойчивую теневую копию, связанную с переменной среды VSS_SHADOW_1, в качестве диска X, введите:
```
expose %vss_shadow_1% x:
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)