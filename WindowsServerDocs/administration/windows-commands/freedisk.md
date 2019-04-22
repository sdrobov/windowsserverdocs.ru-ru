---
title: freedisk
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 91c15166-5baa-4b80-9e0c-4cd815d00530
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 138d637ba3da983ccb931d489f7c22b651e07a0c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59817225"
---
# <a name="freedisk"></a>freedisk

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Проверяет, доступно ли указанный объем места на диске перед продолжением процесса установки.

## <a name="syntax"></a>Синтаксис
```
freedisk [/s <computer> [/u [<Domain>\]<User> [/p [<Password>]]]] [/d <Drive>] [<Value>]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/s <computer>|Указывает имя или IP-адрес удаленного компьютера (не используйте символы обратной косой черты). По умолчанию используется локальный компьютер. Этот параметр применяется ко всем файлам и папкам, указанным в команде.|
|/u [<Domain>\\]<User>|Выполняет сценарий с разрешениями указанной учетной записи. По умолчанию используются системные разрешения.|
|/p [<Password>]|Указывает пароль для учетной записи пользователя, который указан в **/u**.|
|/d <Drive>|Диск, для которого вы хотите проверить доступность свободного пространства. Необходимо указать <Drive>на удаленном компьютере.|
|<Value>|Проверяет наличие определенного объема свободного места на диске. Можно указать <Value>в байтах, КБ, МБ, ГБ, ТБ, PB, EB, ZB или YB.|
## <a name="remarks"></a>Примечания
-   С помощью **/s**, **/u**, и **/p** параметры командной строки доступны только при использовании **/s**. Необходимо использовать **/p** с **/u**пароля пользователя s.
-   для автоматической установки, можно использовать **freedisk** в пакетных файлах для проверки готовности к установке объема свободного пространства перед продолжением установки.
-   При использовании **freedisk** в пакетном файле, он возвращает **0** Если имеется достаточно места и **1** Если не хватает места.
## <a name="BKMK_examples"></a>Примеры
Чтобы определить, будет ли доступно по крайней мере 50 МБ свободного места на диске C:, введите:
```
freedisk 50mb 
```
На экране появится результат, аналогичный приведенному ниже:
```
INFO: The specified 52,428,800 byte(s) of free space is available on current drive.
```
## <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса командной строки](command-line-syntax-key.md)
