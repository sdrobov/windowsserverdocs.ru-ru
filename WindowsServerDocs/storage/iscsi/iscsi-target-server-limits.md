---
title: целевые показатели масштабируемости целевого сервера iSCSI
TOCTitle: iSCSI Target Server Scalability Limits
ms.prod: windows-server-threshold
ms.technology: storage-iscsi
ms.topic: article
author: JasonGerend
manager: dougkim
ms.author: jgerend
ms.date: 09/11/2018
ms.openlocfilehash: 9514392da133911c900f68fc8f1be260b6c91138
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59873035"
---
# <a name="iscsi-target-server-scalability-limits"></a>целевые показатели масштабируемости целевого сервера iSCSI

Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

В этом разделе приведены пределы по целевой сервер поддерживаемых и проверенных iSCSI (Майкрософт) в Windows Server. В следующих таблицах приводятся ограничения протестированных поддержки и, когда это возможно, будет ли предельные значения определяются.

## <a name="general-limits"></a>Общие ограничения

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Элемент</p></th>
<th><p>Ограничения поддержки</p></th>
<th><p>Принудительно?</p></th>
<th><p>Примечание</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>целевые экземпляры iSCSI на сервере цели iSCSI</p></td>
<td><p>256</p></td>
<td><p>Нет</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>iSCSI логические единицы или виртуальных дисков на сервере цели iSCSI</p></td>
<td><p>512</p></td>
<td><p>Нет</p></td>
<td><p>Тестирование настроек включенные: 8 них каждого целевого экземпляра с целевыми объектами среднее более чем 64 и 256 целевые экземпляры с одной LU каждого целевого объекта.</p></td>
</tr>
<tr class="odd">
<td><p>них iSCSI или виртуальных дисков на iSCSI target экземпляра</p></td>
<td><p>256 (128 в Windows Server 2012)</p></td>
<td><p>Да</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Сеансы, которые могут одновременно подключиться к экземпляру целевой объект iSCSI</p></td>
<td><p>544 (512 на Windows Server 2012)</p></td>
<td><p>Да</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Моментальных снимков на LU</p></td>
<td><p>512</p></td>
<td><p>Да</p></td>
<td><p>Ограничено 512 моментальных снимков на том приложения независимых iSCSI.</p></td>
</tr>
<tr class="even">
<td><p>Локально подключенных виртуальных дисков или моментальных снимков на устройстве хранения</p></td>
<td><p>32</p></td>
<td><p>Да</p></td>
<td><p>Локально подключенных виртуальных дисков не предоставляют все функции iSCSI и являются устаревшими — Дополнительные сведения, см. в разделе <a href="https://technet.microsoft.com/library/dn303411.aspx">Features Removed or Deprecated in Windows Server 2012 R2</a>.</p></td>
</tr>
</tbody>
</table>

## <a name="fault-tolerance-limits"></a>Ограничивает устойчивость к сбоям

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Элемент</p></th>
<th><p>Ограничения поддержки</p></th>
<th><p>Принудительно?</p></th>
<th><p>Примечание</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Отказоустойчивые кластеры</p></td>
<td><p>8 (5 на Windows Server 2012)</p></td>
<td><p>Нет</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Несколько активные узлы кластера</p></td>
<td><p>Поддерживается</p></td>
<td> 
<p>Н/Д</p></td>
<td><p>Каждый активный узел в отказоустойчивом кластере владеет кластеризованного экземпляра целевого сервера iSCSI различных с другими узлами, действующий как возможные узлы владельца.</p></td>
</tr>
<tr class="odd">
<td><p>Уровень ошибки восстановления (ERL)</p></td>
<td><p>0</p></td>
<td><p>Да</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Подключения на сеанс</p></td>
<td><p>1</p></td>
<td><p>Да</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Сеансы, которые могут одновременно подключиться к экземпляру целевой объект iSCSI</p></td>
<td><p>544 (512 на Windows Server 2012)</p></td>
<td><p>Нет</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Многопутевого ввода вывода (MPIO)</p></td>
<td><p>Поддерживается</p></td>
<td><p>Н/Д</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Пути MPIO</p></td>
<td><p>4</p></td>
<td><p>Нет</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Преобразование автономного сервера цели iSCSI в кластеризованных iSCSI целевого сервера или наоборот</p></td>
<td><p>Не поддерживается.</p></td>
<td><p>Нет</p></td>
<td><p>ISCSI целевого экземпляра и виртуальный диск данных конфигурации, включая метаданные моментального снимка, будут потеряны во время преобразования.</p></td>
</tr>
</tbody>
</table>

## <a name="network-limits"></a>Ограничения сети

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Элемент</p></th>
<th><p>Ограничения поддержки</p></th>
<th><p>Принудительно?</p></th>
<th><p>Примечание</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Максимальное количество активных сетевых адаптеров</p></td>
<td><p>8</p></td>
<td><p>Нет</p></td>
<td><p>Применяется к сетевым адаптерам, которые выделены для трафика iSCSI, а не общее число сетевых адаптеров на устройстве.</p></td>
</tr>
<tr class="even">
<td><p>Портал (IP-адреса) поддерживается</p></td>
<td><p>64</p></td>
<td><p>Да</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Скорость сети</p></td>
<td><p>40Gbps 1 Гбит/с, 10 Гбит/с, 56 Гбит/с (Windows Server 2012 R2 и более поздних версий только)</p></td>
<td><p>Нет</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>IPv4</p></td>
<td><p>Поддерживается</p></td>
<td><p>Н/Д</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>IPv6</p></td>
<td><p>Поддерживается</p></td>
<td><p>Н/Д</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Разгрузка TCP</p></td>
<td><p>Поддерживается</p></td>
<td><p>Н/Д</p></td>
<td><p>Использовать большой отправки (сегментация), контрольная сумма, прерываниями и разгрузки RSS</p></td>
</tr>
<tr class="odd">
<td><p>Разгрузка iSCSI</p></td>
<td><p>Не поддерживается.</p></td>
<td>              
<p>Н/Д</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Кадры крупного размера</p></td>
<td><p>Поддерживается</p></td>
<td><p>Н/Д</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>IPSec</p></td>
<td><p>Поддерживается</p></td>
<td><p>Н/Д</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Разгрузка контрольной СУММЫ</p></td>
<td><p>Поддерживается</p></td>
<td><p>Н/Д</p></td>
<td></td>
</tr>
</tbody>
</table>

## <a name="iscsi-virtual-disk-limits"></a>ограничения виртуального диска iSCSI

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Элемент</p></th>
<th><p>Ограничения поддержки</p></th>
<th><p>Принудительно?</p></th>
<th><p>Примечание</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Из iSCSI-инициатора преобразования виртуального диска с собой базовый диск в динамический диск </p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Формат виртуального жесткого диска.</p></td>
<td><p>.vhdx (Windows Server 2012 R2 и более поздних версий только)</p>
<p>.vhd</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Формат минимальный размер виртуального жесткого диска</p></td>
<td><p>.vhdx: 3 MБ</p>
<p>.vhd: 8 МБ</p></td>
<td><p>Да</p></td>
<td><p>Применяется для всех поддерживаемых типов виртуального жесткого диска: родительский элемент, разностные и исправлена.</p></td>
</tr>
<tr class="even">
<td><p>Максимальный размер родительского виртуального жесткого диска</p></td>
<td><p>.vhdx: 64 ТБ</p>
<p>.vhd: 2 ТБ</p></td>
<td><p>Да</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Фиксированный максимальный размер виртуального жесткого диска</p></td>
<td><p>.vhdx: 64 ТБ</p>
<p>.vhd: 16 ТБ</p></td>
<td><p>Да</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Максимальный размер разностного виртуального жесткого диска</p></td>
<td><p>.vhdx: 64 ТБ</p>
<p>.vhd: 2 ТБ</p></td>
<td><p>Да</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Фиксированный формат виртуального жесткого диска</p></td>
<td><p>Поддерживается</p></td>
<td><p>Нет</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Формат разностный виртуальный жесткий ДИСК</p></td>
<td><p>Поддерживается</p></td>
<td><p>Нет</p></td>
<td><p>Моментальные снимки нельзя создавать разностных виртуальных дисков iSCSI на основе виртуального жесткого диска.</p></td>
</tr>
<tr class="odd">
<td><p>Число разностные виртуальные жесткие диски на родительского виртуального жесткого диска</p></td>
<td><p>256</p></td>
<td><p>Нет (Да, в Windows Server 2012)</p></td>
<td><p>Два уровня глубины (внучатых vhdx-файлы) является максимальным значением для vhdx-файлы; один уровень глубины (дочерних VHD-файлы) является максимальным для VHD-файлы.</p></td>
</tr>
<tr class="even">
<td><p>Динамический формат виртуального жесткого диска</p></td>
<td><p>.vhdx: Да</p>
<p>.vhd: Да (нет на Windows Server 2012)</p></td>
<td><p>Да</p></td>
<td><p>Отмена сопоставления не поддерживается.</p></td>
</tr>
<tr class="odd">
<td><p>exFAT/FAT32 и FAT (при размещении тома виртуального жесткого диска)</p></td>
<td><p>Не поддерживается.</p></td>
<td><p>Да</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>CSV v2</p></td>
<td><p>Не поддерживается.</p></td>
<td><p>Да</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>ReFS</p></td>
<td><p>Поддерживается</p></td>
<td><p>Н/Д</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>NTFS</p></td>
<td><p>Поддерживается</p></td>
<td><p>Н/Д</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>CFS, отличных от Microsoft</p></td>
<td><p>Не поддерживается.</p></td>
<td><p>Да</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Тонкая подготовка</p></td>
<td><p>Нет</p></td>
<td><p>Н/Д</p></td>
<td><p>Динамические виртуальные жесткие диски поддерживаются, но операций Unmap не поддерживается.</p></td>
</tr>
<tr class="odd">
<td><p>Логические единицы сжатия</p></td>
<td><p>Да (Windows Server 2012 R2 и более поздних версий только)</p></td>
<td><p>Н/Д</p></td>
<td><p>Используйте <a href="https://docs.microsoft.com/powershell/module/iscsitarget/resize-iscsivirtualdisk">Resize-iSCSIVirtualDisk</a> сжатие LUN.</p></td>
</tr>
<tr class="even">
<td><p>Клонирование логического устройства</p></td>
<td><p>Не поддерживается.</p></td>
<td><p>Н/Д</p></td>
<td><p>Вы можете быстро клонировать данные диска с помощью разностных виртуальных жестких дисков.</p></td>
</tr>
</tbody>
</table>

## <a name="snapshot-limits"></a>Ограничения по числу моментальных снимков

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Элемент</p></th>
<th><p>Ограничения поддержки</p></th>
<th><p>Примечание</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Создание моментального снимка</p></td>
<td><p>Поддерживается</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Восстановление моментального снимка</p></td>
<td><p>Поддерживается</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Для записи моментальных снимков</p></td>
<td><p>Не поддерживается.</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Моментальный снимок — преобразовать в полную</p></td>
<td><p>Не поддерживается.</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Моментальный снимок — online отката</p></td>
<td><p>Не поддерживается.</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Моментальный снимок — преобразование в доступный для записи</p></td>
<td><p>Не поддерживается.</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Моментальный снимок — перенаправление</p></td>
<td><p>Не поддерживается.</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Моментальный снимок - закрепления</p></td>
<td><p>Не поддерживается.</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Локального подключения</p></td>
<td><p>Поддерживается</p></td>
<td><p>Являются устаревшими виртуальными дисками iSCSI с локально подключенного — Дополнительные сведения см. в <a href="https://technet.microsoft.com/library/dn303411.aspx">Features Removed or Deprecated in Windows Server 2012 R2</a>. Моментальные снимки динамического диска невозможно подключить локально.</p></td>
</tr>
</tbody>
</table>

## <a name="iscsi-target-server-manageability-and-backup"></a>управляемость сервера цели iSCSI и резервного копирования

Если вы хотите создать теневые копии (моментальные снимки VSS открытого файла) данных тома на виртуальных дисках iSCSI на сервере приложений или вы хотите управлять виртуальными дисками iSCSI с помощью более старые приложения (например, команда Diskraid), которое требует оборудования службы виртуальных дисков (VDS) Поставщик, установите поставщик хранилища цели iSCSI на сервере, из которого вы хотите создать моментальный снимок или использовать приложение управления VDS.

Поставщик хранилища цели iSCSI — это служба роли в Windows Server 2016, Windows Server 2012 R2 и Windows Server 2012; Можно также загрузить и установить [iSCSI Target поставщиков хранилища (VDS и VSS) для серверов приложений нижнего уровня](http://www.microsoft.com/download/details.aspx?id=34759) следующих операционных системах, пока конечный iSCSI-сервер работает в Windows Server 2012:

  - Windows Storage Server 2008 R2

  - Windows Server 2008 R2

  - Windows HPC Server 2008 R2

  - Windows HPC Server 2008

Обратите внимание, что если сервер цели iSCSI, размещенной на сервере под управлением Windows Server 2012 R2 или более поздней версии, и вы хотите использовать VSS и VDS с удаленного сервера, сервер также выполните ту же версию Windows Server и службы роли поставщика хранилища цели iSCSI e установлен. Обратите внимание на то, что во всех версиях Windows следует установить только одну версию служба роли поставщика хранилища цели iSCSI.

Дополнительные сведения о поставщик хранилища цели iSCSI, см. в разделе [поставщик целевого хранилища (VDS и VSS) iSCSI](http://blogs.technet.com/b/filecab/archive/2012/10/08/iscsi-target-storage-vds-vss-provider.aspx).

## <a name="tested-compatibility-with-iscsi-initiators"></a>Протестированные совместимость с инициаторы iSCSI

Мы протестировали iSCSI программного обеспечения целевого сервера с помощью следующих инициаторы iSCSI:

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Инициатор</p></td>
<td><p>Windows Server 2012 R2</p></td>
<td><p>Windows Server 2012</p></td>
<td><p>Комментарии</p></td>
</tr>
<tr class="even">
<td><p>Windows Server 2012 R2</p></td>
<td><p>Проверено</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Windows Server 2012, Windows Server 2008 R2, Windows Server 2008, Windows Server 2003</p></td>
<td><p>Проверено</p></td>
<td><p>Проверено</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>VMWare vSphere 5</p></td>
<td></td>
<td><p>Проверено</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>VMWare ESXi 5.0</p></td>
<td><p>Проверено</p></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>VMWare ESX 4.1</p></td>
<td><p>Проверено</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>CentOS 6.x</p></td>
<td><p>Проверено</p></td>
<td></td>
<td><p>Необходимо выйти из сеанса и снова войдите в систему обнаружения измененного размера виртуального диска.</p></td>
</tr>
<tr class="even">
<td><p>Red Hat Enterprise Linux 6</p></td>
<td><p>Проверено</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Red Hat Enterprise Linux 5 и 5</p></td>
<td><p>Проверено</p></td>
<td><p>Проверено</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>SUSE Linux Enterprise Server 10</p></td>
<td></td>
<td><p>Проверено</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Oracle Solaris 11.x</p></td>
<td><p>Проверено</p></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Кроме того, мы протестировали следующие инициаторы iSCSI, выполняющем бездисковой загрузки виртуальных дисков, расположенных на сервере цели iSCSI:

  - Windows Server 2012 R2

  - Windows Server 2012

  - Сетевой КАРТОЙ и PCIe iPXE

  - Компакт-ДИСК или USB-диск с iPXE

## <a name="see-also"></a>См. также

Ниже перечислены дополнительные ресурсы с информацией о сервере цели iSCSI и связанных технологиях.

  - [Обзор блочного хранилища цели iSCSI](iscsi-target-server.md)

  - [Обзор загрузки цели iSCSI](iscsi-boot-overview.md)

  - [Хранилища в Windows Server](..\storage.md)

