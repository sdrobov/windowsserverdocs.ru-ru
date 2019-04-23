---
title: auditpol
description: Раздел Windows команды для **auditpol** — отображает сведения о и выполняет функции управления политики аудита.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a02cfb9d-732f-4e77-aeba-f18265daa3af
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d7e8364be977e868ac161704e67c37ec5c400e49
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59849225"
---
# <a name="auditpol"></a>auditpol



Отображает сведения о и выполняет функции управления политики аудита.

Примеры использования этой команды см. в разделе в подразделе "Примеры" каждого раздела.

## <a name="syntax"></a>Синтаксис

```
Auditpol command [<sub-command><options>]
```

## <a name="parameters"></a>Параметры

|Подкоманда|Описание|
|-----------|-----------|
|/ Get /|Отображает текущую политику аудита.</br>См. в разделе [Auditpol get](auditpol-get.md) синтаксис и параметры.|
|/ set|Задает политику аудита.</br>См. в разделе [Auditpol set](auditpol-set.md) синтаксис и параметры.|
|/ List|Отображает элементы, доступный для выбора политики.</br>См. в разделе [Auditpol list](auditpol-list.md) синтаксис и параметры.|
|/ backup|Сохраняет файл политики аудита.</br>См. в разделе [резервного копирования Auditpol](auditpol-backup.md) синтаксис и параметры.|
|/ RESTORE|Восстанавливает политику аудита из файла, который был создан ранее с помощью средства auditpol/Backup.</br>См. в разделе [восстановления Auditpol](auditpol-restore.md) синтаксис и параметры.|
|/ clear|Удаляет политику аудита.</br>См. в разделе [Auditpol Очистить](auditpol-clear.md) синтаксис и параметры.|
|/remove|Удаляет все параметры политики аудита на пользователя и отключает все параметры политики аудита системы.</br>См. в разделе [Auditpol remove](auditpol-remove.md) синтаксис и параметры.|
|/resourceSACL|Настройка глобальных ресурсов системы управления доступом (SACL).</br>Примечание. Применяется только к Windows 7 и Windows Server 2008 R2.</br>См. в разделе [Auditpol resourceSACL](auditpol-resourcesacl.md).|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

Средство командной строки политики аудита может использоваться для:
-   Устанавливать и запрашивать политики аудита системы.
-   Устанавливать и запрашивать политики аудита на пользователя.
-   Устанавливать и запрашивать параметры аудита.
-   Устанавливать и запрашивать дескриптор безопасности, используемые для делегирования доступа к политики аудита.
-   Сообщить о или резервного копирования политики аудита в текстовый файл значений с разделителями запятыми (CSV).
-   Загрузите политику аудита из текстового файла CSV.
-   Настройка глобальных ресурсов системных списков управления доступом.

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)