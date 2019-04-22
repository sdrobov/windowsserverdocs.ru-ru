---
title: change port
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3d772c90-e849-4e74-b9ec-b6cae1159336 Lizap
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 477761c35f08d5ec81adae80ba8f2fe9667786e9
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59818645"
---
# <a name="change-port"></a>change port

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает и изменяет сопоставления COM-портов для совместимости с приложениями MS-DOS.
Примеры для использования этой команды, см. в разделе [примеры](#BKMK_examples).
> [!NOTE]
> В Windows Server 2008 R2 службы терминалов были переименованы на службы удаленных рабочих столов. Чтобы найти новые возможности в последней версии, см. в разделе [какие возможности служб удаленных рабочих столов в Windows Server 2012](https://technet.microsoft.com/library/hh831527) в технической библиотеке Windows Server.
## <a name="syntax"></a>Синтаксис
```
change port [<PortX>=<PortY> | /d <PortX> | /query]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|<PortX>=<PortY>|Сопоставляет COM <*PortX*> для <*PortY*>.|
|/d <PortX>|Удаление сопоставления для модели COM <*PortX*>.|
|/ Query|Отображает текущее сопоставление портов.|
|/?|Отображение справки в командной строке.|
## <a name="remarks"></a>Примечания
-   Большинство приложений MS-DOS поддерживают только COM1 – COM4 последовательных портов. **Изменить порт** команда сопоставляет последовательный порт для другой номер порта, позволяет приложениям, не поддерживают COM высокими номерами портов для доступа к последовательному порту. повторное сопоставление работает только для текущего сеанса и не сохраняются, если выйти из сеанса и затем повторно выполнить вход.
-   Используйте **изменение порта** без параметров для отображения доступных Последовательных портов и их текущего сопоставления.
## <a name="BKMK_examples"></a>Примеры
-   Чтобы сопоставить COM12 COM1 для использования в приложении на основе MS-DOS, введите следующую команду:
    ```
    change port com12=com1
    ```
-   Чтобы отобразить текущее сопоставление портов, введите следующую команду:
    ```
    change port /query
    ```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[изменить](change.md)
[служб удаленных рабочих столов &#40;служб терминалов&#41; Справочник по командам](remote-desktop-services-terminal-services-command-reference.md)
