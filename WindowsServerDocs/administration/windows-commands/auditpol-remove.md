---
title: Удаление средства Auditpol
description: Раздел Windows команды для **удалить auditpol** -удаляет политику аудита пользователя для указанной учетной записи или все учетные записи.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: be42ec55-235c-44f7-9abd-ed1cf3f5b1f5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 566827e93d9f8c9dc0d00f4f704513369fbb44ad
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59818305"
---
# <a name="auditpol-remove"></a>Удаление средства Auditpol

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет политику аудита пользователя для указанной учетной записи или все учетные записи.

## <a name="syntax"></a>Синтаксис
```
auditpol /remove [/user[:<username>|<{SID}>]]
[/allusers]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/ User|Указывает идентификатор безопасности (SID) или имя пользователя для пользователя, для которого политики аудита на пользователя — для удаления.|
|/ALLUSERS|Удаляет политику аудита пользователя для всех пользователей.|
|/?|Отображение справки в командной строке.|
## <a name="remarks"></a>Примечания
для операций удаления для политики пользователя необходимо иметь разрешение записи или полного доступа на этот объект, задайте в дескрипторе безопасности. Можно также выполнить операции удаления, исходя из **Управление аудитом и журналом безопасности** право пользователя (SeSecurityPrivilege). Тем не менее это право позволяет дополнительные права доступа, которые не являются необходимыми для выполнения операции удаления.
## <a name="BKMK_examples"></a>Примеры
Чтобы удалить политику аудита пользователя для пользователя mikedan по имени, введите следующую команду:
```
auditpol /remove /user:mikedan
```
Чтобы удалить политику аудита пользователя для пользователя mikedan по SID, введите:
```
auditpol /remove /user:{S-1-5-21-397123471-12346959}
```
Чтобы удалить политику аудита пользователя для всех пользователей, введите:
```
auditpol /remove /allusers
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса командной строки](command-line-syntax-key.md)
