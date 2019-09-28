---
title: auditpol
description: Раздел команд Windows для **auditpol** — отображает сведения о и выполняет функции для управления политиками аудита.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 5e249a9e2a07505f052b774208c514b4d16879b8
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71382377"
---
# <a name="auditpol"></a>auditpol



Отображает сведения о и выполняет функции для управления политиками аудита.

Примеры использования этой команды см. в разделе "примеры" в каждом разделе.

## <a name="syntax"></a>Синтаксис

```
Auditpol command [<sub-command><options>]
```

## <a name="parameters"></a>Параметры

|Подкоманда|Описание|
|-----------|-----------|
|/Get|Отображает текущую политику аудита.</br>Синтаксис и параметры см. в разделе [auditpol Get](auditpol-get.md) .|
|команде|Задает политику аудита.</br>Синтаксис и параметры см. в разделе [auditpol Set](auditpol-set.md) .|
|/List|Отображает выбираемые элементы политики.</br>Синтаксис и параметры см. в разделе [auditpol list](auditpol-list.md) .|
|/баккуп|Сохраняет политику аудита в файл.</br>Синтаксис и параметры см. в разделе [auditpol backup](auditpol-backup.md) .|
|/Restore|Восстанавливает политику аудита из файла, созданного ранее с помощью Auditpol/баккуп.</br>Синтаксис и параметры см. в разделе [auditpol restore](auditpol-restore.md) .|
|/Clear|Очищает политику аудита.</br>Синтаксис и параметры см. в разделе [auditpol Clear](auditpol-clear.md) .|
|/remove|Удаляет все параметры политики аудита для каждого пользователя и отключает все параметры политики аудита системы.</br>Синтаксис и параметры см. в разделе [auditpol Remove](auditpol-remove.md) .|
|/ресаурцесакл|Настраивает списки управления доступом к глобальным ресурсам системы (SACL).</br>Примечание. Применимо только к Windows 7 и Windows Server 2008 R2.</br>См. раздел [auditpol ресаурцесакл](auditpol-resourcesacl.md).|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

Программу командной строки политики аудита можно использовать для:
-   Установка и запрос политики аудита системы.
-   Задайте и запросите политику аудита для каждого пользователя.
-   Установка и запрос параметров аудита.
-   Задайте и запросите дескриптор безопасности, используемый для делегирования доступа к политике аудита.
-   Отчет или резервная копия политики аудита в текстовом файле с разделителями-запятыми (CSV).
-   Загрузка политики аудита из текстового файла CSV.
-   Настройка списков SACL глобальных ресурсов.

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)