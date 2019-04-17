---
title: "Управление дисками"
description: "В этой статье описывается, как управлять дисками"
ms.date: 10/12/2017
ms.prod: windows-server-threshold
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: ae96071733b961fbe65551120894c21c633db83e
ms.sourcegitcommit: 583355400f6b0d880dc0ac6bc06f0efb50d674f7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2017
---
# <a name="manage-disks"></a>Управление дисками

> **Область применения:** Windows 10, Windows 8.1, Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

В этом разделе и его подразделах описывается использование средства управления дисками для управления дисками в компьютере, а также содержатся сведения об изменении стиля раздела дисков и об особенностях обработки подключенного состояния новых дисков в Windows.

## <a name="converting-disk-types"></a>Преобразование типов дисков

Несмотря на то, что средство управления дисками дает возможность изменять типы дисков и стили раздела, некоторые операции необратимы без повторного форматирования диска. Внимательно выберите оптимальный для ваших потребностей тип диска и стиль раздела.

В следующей таблице представлены варианты преобразования стиля раздела дисков.

| Тип диска | Преобразование в MBR  | Преобразование в GPT| Преобразование в динамический диск |
| ---- | --- | --- |--- |
| <p>Основная загрузочная запись (MBR)</p> | <p>--</p> | <p>Разрешено (при отсутствии на диске томов).</p> | <p>Разрешено, но диск может стать незагружаемым. См. примечание.</p> |
| <p>Таблица разделов GUID (GPT).</p> | <p>Разрешено (при отсутствии на диске томов).</p> | <p>--</p>  | <p>Разрешено, но диск может стать незагружаемым. См. примечание.</p> |


> [!NOTE]
> В сценарии с загрузкой нескольких ОС, если загрузить одну операционную систему и преобразовать базовый диск MBR, содержащий другую операционную систему, в динамический диск, загрузка второй операционной системы станет невозможна.

## <a name="online-and-offline-status"></a>Подключенное и отключенное состояние

Средство управления дисками отображает подключенное и отключенное состояния дисков. 

По умолчанию в Windows все недавно обнаруженные диски подключаются с доступом для чтения и записи. По умолчанию в Windows Server недавно обнаруженные диски подключаются с доступом для чтения и записи, если они не находятся на обще шине (такой как SCSI, iSCSI, Serial Attached SCSI или Fibre Channel) Диски на общей шине при первом подключении будут отключены.

Если диск отключен, перед инициализацией или созданием на нем томов его необходимо подключить. 

-  Для подключения или отключения диска щелкните правой кнопкой мыши имя диска и выберите соответствующее действие.

## <a name="see-also"></a>См. также

-   [Инициализация новых дисков](initialize-new-disks.md)
-   [Перемещение дисков на другой компьютер](move-disks-to-another-computer.md)
-   [Преобразование динамического диска в базовый](change-a-dynamic-disk-back-to-a-basic-disk.md)
-   [Изменение стиля раздела диска с основной загрузочной записи на таблицу разделов GUID](change-an-mbr-disk-into-a-gpt-disk.md)
-   [Изменение стиля раздела диска с таблицы разделов GUID на основную загрузочную запись](change-a-gpt-disk-into-an-mbr-disk.md)
-   [Управление виртуальными жесткими дисками](manage-virtual-hard-disks.md)