---
title: удалить Auditpol
description: Раздел команд Windows для средства **auditpol Remove**, удаляющий политику аудита для каждого пользователя для указанной учетной записи или для всех учетных записей.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: be42ec55-235c-44f7-9abd-ed1cf3f5b1f5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1eda43d6708a31b2966022d2ae2c162bbfc888cb
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851177"
---
# <a name="auditpol-remove"></a>удалить Auditpol

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет политику аудита "на пользователя" для указанной учетной записи или всех учетных записей.

## <a name="syntax"></a>Синтаксис

```
auditpol /remove [/user[:<username>|<{SID}>]]
[/allusers]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| ------- | -------- |
| WMIC | Указывает идентификатор безопасности (SID) или имя пользователя для пользователя, для которого необходимо удалить политику аудита на пользователя. |
| /аллусерс | Удаляет политику аудита для каждого пользователя для всех пользователей. |
| /? | Отображает справку в командной строке. |

## <a name="remarks"></a>Примечания

Для операций удаления для политики на пользователя необходимо иметь разрешение на запись или полный доступ для этого набора объектов в дескрипторе безопасности. Операции удаления также можно выполнять, нажимая прав пользователя " **Управление аудитом и журналом безопасности** " (SeSecurityPrivilege). Однако это право позволяет получить дополнительный доступ, который не требуется для выполнения операции удаления.

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы удалить политику аудита "на пользователя" для пользователя микедан по имени, введите:

```
auditpol /remove /user:mikedan
```

Чтобы удалить политику аудита "на пользователя" для пользователя микедан по идентификатору безопасности, введите:

```
auditpol /remove /user:{S-1-5-21-397123471-12346959}
```

Чтобы удалить политику аудита для каждого пользователя для всех пользователей, введите:

```
auditpol /remove /allusers
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
