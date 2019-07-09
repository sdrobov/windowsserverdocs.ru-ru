---
title: Управление дисками
description: В этой статье описывается, как управлять дисками
ms.date: 06/07/2019
ms.prod: windows-server-threshold
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 344dd363e970b195abe20fcb69e741c450fc7a21
ms.sourcegitcommit: 3743cf691a984e1d140a04d50924a3a0a19c3e5c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2019
ms.locfileid: "66812408"
---
# <a name="manage-disks"></a>Управление дисками

> **Относится к:** Windows 10, Windows 8.1, Windows Server (Semi-Annual Channel), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

В этом разделе и его подразделах описывается использование средства управления дисками для управления дисками в компьютере, а также содержатся сведения об инициализации новых дисков, изменении стиля раздела дисков и об особенностях обработки подключенного состояния новых дисков в Windows.

## <a name="online-and-offline-status"></a>Подключенное и отключенное состояние

Управление дисками отображает сведения о том, находится диск в подключенном или в отключенном состоянии.

По умолчанию в Windows все недавно обнаруженные диски подключаются с доступом для чтения и записи. По умолчанию в Windows Server недавно обнаруженные диски подключаются с доступом для чтения и записи, если они не находятся на обще шине (такой как SCSI, iSCSI, Serial Attached SCSI или Fibre Channel). Диски на общей шине при первом подключении будут отключены.

Если диск отключен, перед инициализацией или созданием на нем томов его необходимо подключить.

Для подключения или отключения диска щелкните правой кнопкой мыши имя диска и выберите соответствующее действие.

## <a name="see-also"></a>См. также

-   [Инициализация новых дисков](initialize-new-disks.md)
-   [Перемещение дисков на другой компьютер](move-disks-to-another-computer.md)
-   [Преобразование динамического диска в базовый](change-a-dynamic-disk-back-to-a-basic-disk.md)
-   [Изменение стиля раздела диска с основной загрузочной записи на таблицу разделов GUID](change-an-mbr-disk-into-a-gpt-disk.md)
-   [Изменение стиля раздела диска с таблицы разделов GUID на основную загрузочную запись](change-a-gpt-disk-into-an-mbr-disk.md)
-   [Управление виртуальными жесткими дисками](manage-virtual-hard-disks.md)