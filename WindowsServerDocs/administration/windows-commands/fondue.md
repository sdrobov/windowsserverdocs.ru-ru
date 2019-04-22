---
title: fondue
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fc4467f6-ddbb-4d6d-b51e-5a50a957b8c0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 09708c239b5399f3284c42877970443cc2605cbe
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59817155"
---
# <a name="fondue"></a>fondue

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Включает дополнительные компоненты Windows, скачав необходимые файлы из центра обновления Windows или другого источника, заданного параметром групповой политики. Файл манифеста для функции должна быть установлена в образе Windows. 
## <a name="syntax"></a>Синтаксис
```
fondue.exe /enable-feature:<feature_name> [/caller-name:<program_name>] [/hide-ux:{all | rebootRequest}]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/enable-feature:<*feature_name*>|Задает имя используемого дополнительный компонент Windows, которые вы хотите включить. Можно включить только одну функцию в командной строке. Чтобы включить несколько компонентов, для каждого компонента оставьте fondue.exe.|
|/CALLER-Name: <*имя_программы*>|Указывает имя программа или процесс, при вызове fondue.exe из сценария или пакетного файла. Этот параметр можно использовать для добавления имени программы отчета SQM, если возникает ошибка.|
|/hide-ux:{all &#124; rebootRequest}|Используйте **все** Чтобы скрыть все сообщения, включая запросы ход выполнения и разрешение на доступ к Windows Update. Если требуется разрешение, операция завершится ошибкой.<br /><br />Используйте **rebootRequest** только скрыть сообщения пользователя, запрашивает разрешение на перезагрузку компьютера. Используйте этот параметр, если у вас есть сценарий, что элементы управления перезагрузите запросов.|
## <a name="BKMK_Examples"></a>Примеры
Чтобы включить Microsoft .NET Framework 3.5, введите следующую команду:
```
fondue.exe /enable-feature:NETFX3
```
Чтобы включить Microsoft .NET Framework 3.5, добавьте имя программы для отчета SQM и не отображать сообщения для пользователя, тип:
```
fondue.exe /enable-feature:NETFX3 /caller-name:Admin.bat /hide-ux:all
```
## <a name="additional-references"></a>Дополнительные ссылки
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)
## <a name="see-also"></a>См. также
[Рекомендации по развертыванию Microsoft .NET Framework 3.5](https://go.microsoft.com/fwlink/?LinkId=248869)
