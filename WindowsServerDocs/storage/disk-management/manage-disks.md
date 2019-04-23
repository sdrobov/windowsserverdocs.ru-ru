---
title: Управление дисками
description: В этой статье описывается, как управлять дисками
ms.date: 12/21/2017
ms.prod: windows-server-threshold
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: f4698dac683ff3769eb4403ae2750ad38a301022
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59846195"
---
# <a name="manage-disks"></a>Управление дисками

> **Область применения:** Windows 10, Windows 8.1, Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Этот раздел и его подразделы обсудить с помощью управления дисками для управления дисками на компьютере и включает сведения об инициализации новых дисков, преобразование дисков между стилями отдельной секции, и как Windows обрабатывает состояние новых дисков.

## <a name="online-and-offline-status"></a>Подключенное и отключенное состояние

Управление дисками, отображает ли диск находится в сети (доступно), или в автономном режиме.

По умолчанию в Windows все недавно обнаруженные диски подключаются с доступом для чтения и записи. По умолчанию в Windows Server недавно обнаруженные диски подключаются с доступом для чтения и записи, если они не находятся на обще шине (такой как SCSI, iSCSI, Serial Attached SCSI или Fibre Channel) Диски на общей шине находятся в автономном режиме при первом их обнаружения.

Если диск отключен, перед инициализацией или созданием на нем томов его необходимо подключить.

Чтобы перевести диск в оперативный режим или перевести в автономный режим, щелкните правой кнопкой мыши имя диска и выбрав соответствующие действия.





## <a name="see-also"></a>См. также

-   [Инициализация нового диска](initialize-new-disks.md)
-   [Перемещение дисков на другой компьютер](move-disks-to-another-computer.md)
-   [Измените способ динамического диска на базовом диске](change-a-dynamic-disk-back-to-a-basic-disk.md)
-   [Преобразование диска основная загрузочная запись в таблицу разделов GUID](change-an-mbr-disk-into-a-gpt-disk.md)
-   [Преобразование диска таблица разделов GUID с основной загрузочной записи](change-a-gpt-disk-into-an-mbr-disk.md)
-   [Управление виртуальными жесткими дисками](manage-virtual-hard-disks.md)