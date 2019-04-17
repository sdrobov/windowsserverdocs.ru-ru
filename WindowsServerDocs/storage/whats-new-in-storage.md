---
ms.assetid: 0f2a7f7b-aca8-4e5d-ad67-4258e88bc52f
title: "Новые возможности хранилища в Windows Server"
ms.prod: windows-server-threshold
ms.author: jgerend
ms.manager: dongill
ms.technology: storage
ms.topic: article
author: kumudd
ms.date: 09/15/2016
ms.openlocfilehash: 9aab6246f7ddc86629834bf20a7d21cc4ce2ec8f
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="whats-new-in-storage-in-windows-server-2016"></a>Новые возможности хранилища в Windows Server 2016

>Область применения: Windows Server 2016

В этой статье приводятся сведения о новых и измененных функциях хранилища в Windows Server 2016.

## <a name="s2d"></a>Локальные дисковые пространства  
Локальные дисковые пространства позволяют создавать масштабируемые хранилища с высоким уровнем доступности с помощью серверов с локальным хранилищем. Они упрощают развертывание и администрирование программно-определяемых систем хранения данных и открывают возможность использования дисковых устройств новых классов, например SATA SSD и NVMe. Ранее для кластерных дисковых пространств с общими дисками это было невозможно.  

**Какой эффект дает это изменение?**  
Локальные дисковые пространства дают возможность поставщикам услуг и предприятиям использовать стандартные для отрасли серверы с локальным хранилищем для создания масштабируемого программно-определяемого хранилища с высоким уровнем доступности. Использование серверов с локальным хранилищем упрощает организацию данных, повышает масштабируемость хранилища и позволяет использовать запоминающие устройства, которые ранее были недоступны, например твердотельные накопители SATA. Таким образом, сокращаются затраты на флэш-накопители или твердотельные накопители NVMe, повышающие производительность.  

Локальные дисковые пространства избавляют от необходимости использования общей структуры хранилища SAS, упрощая развертывание и настройку. Вместо этого в качестве структуры хранилища используется сеть, а протоколы SMB3 и SMB Direct (RDMA) обеспечивают высокую скорость передачи данных, небольшую задержку и рациональное использование процессора. Чтобы масштабировать хранилище, нужно просто добавить дополнительные серверы для увеличения емкости и повышения производительности операций ввода-вывода.  
Дополнительные сведения см. в статье [Storage Spaces Direct in Windows Server2016](storage-spaces/storage-spaces-direct-overview.md) (Локальные дисковые пространства в Windows Server2016).  

**Что работает иначе?**  
Это новая функция в Windows Server2016.  

## <a name="storage-replica"></a>Реплика хранилища  
Реплика хранилища реализует независимую от хранилища синхронную репликацию между серверами или кластерами на уровне блоков для аварийного восстановления, а также растягивание отказоустойчивого кластера между сайтами. Синхронная репликация позволяет зеркально отображать данные в физических расположениях с отказоустойчивыми томами, что полностью предотвращает потерю данных на уровне файловой системы. Асинхронная репликация позволяет использовать физические расположения за пределами города, но при этом вероятна потеря данных.  

**Какой эффект дает это изменение?**  
Репликация хранилища предоставляет следующие возможности.  

* Предоставление решения по аварийному восстановлению данных от одного поставщика при запланированных и незапланированных сбоях критически важных приложений.
* Использование транспортного протокола SMB3 с доказанной надежностью, масштабируемостью и производительностью.
* Расширение отказоустойчивых кластеров Windows до городской сети.
* Комплексное использование программного обеспечения Майкрософт для хранения и кластеризации, в частности Hyper-V, реплик хранилища, дисковых пространств, кластера, масштабируемого файлового сервера, SMB3, дедупликации и ReFS/NTFS.
* Сокращение затрат и уменьшение сложности следующим образом: 
    * Хранилище не зависит от оборудования, отсутствуют строгие требования к конфигурации хранилища (DAS или SAN).
    * Разрешается использовать стандартные технологии хранения и сетевых подключений.
    * Управление отдельными узлами и кластерами осуществляется в удобной графической среде с помощью диспетчера отказоустойчивости кластеров.
    * Функция включает в себя возможность создания комплексных крупномасштабных скриптов с помощью Windows PowerShell. 
* Способствует сокращению времени простоев и повышению свойственной Windows надежности и производительности.  
* Обеспечивает поддержку, диагностику и определение метрик производительности.  

Дополнительные сведения см. в разделе [Реплика хранилища в Windows Server2016](storage-replica/storage-replica-overview.md).  

**Что работает иначе?**  
Это новая функция в Windows Server2016.  

## <a name="storage-qos"></a>Качество обслуживания хранилища  
Функцию качества обслуживания хранилища (QoS) теперь можно использовать для централизованного отслеживания общей производительности хранилища, а также для создания политик управления с помощью Hyper-V и кластеров CSV в Windows Server2016.  

**Какой эффект дает это изменение?**  
Теперь можно создавать политики качества обслуживания хранилища в кластере CSV и назначить их одному или нескольким виртуальным дискам на виртуальных машинах Hyper-V. Производительность хранилища автоматически переопределяется в соответствии с политиками по мере колебания рабочих нагрузок и объемов загрузки хранилища.  

* Каждая политика может определять резерв (минимум) и предел (максимум), которые применяются к коллекции потоков данных, например к виртуальному жесткому диску, одной виртуальной машине или группе виртуальных машин, службе или клиенту.  
* С помощью Windows PowerShell или WMI можно выполнять следующие задачи:  
    * создание политик в кластере CSV;
    * перечисление политик, доступных в кластере CSV;
    * назначение политики виртуальному жесткому диску в виртуальной машине Hyper-V; 
    * мониторинг производительности и состояния каждого потока в рамках политики.  
* Если несколько виртуальных жестких дисков используют одну и ту же политику, производительность распределяется равномерно в соответствии с потребностями в рамках минимальных и максимальных значений, предусмотренных политикой. Таким образом, политика может использоваться для управления виртуальным жестким диском, виртуальной машиной, несколькими виртуальными машинами, составляющими службу, или всеми виртуальными машинами клиента.  

**Что работает иначе?**  
Это новая функция в Windows Server2016. Управление минимальными резервами, мониторинг потоков всех виртуальных жестких дисков в кластере с помощью одной команды и централизованное управление на основе политик были невозможны в предыдущих выпусках Windows Server.  

Дополнительные сведения см. в статье о [качестве обслуживания хранилища](storage-qos/storage-qos-overview.md).

## <a name="dedup"></a>Дедупликация данных  
| Функции | Новая или обновленная | Описание |
|---------------|----------------|-------------|
| [Поддержка больших томов](data-deduplication/whats-new.md#large-volume-support) | Обновлено | До выхода Windows Server2016 приходилось подгонять размер тома к масштабу обработки, при этом том с размером больше 10ТБ обычно не подходил для дедупликации данных. В Windows Server2016 дедупликация данных поддерживает тома размером **до 64ТБ**. |
| [Поддержка больших файлов](data-deduplication/whats-new.md#large-file-support) | Обновлено | До выпуска Windows Server2016 файлы с размером около 1ТБ обычно не подходили для дедупликации данных. В Windows Server2016 файлы размером **до 1ТБ** полностью поддерживаются. |
| [Поддержка Nano Server](data-deduplication/whats-new.md#nano-server-support) | Создать | Дедупликация данных полностью поддерживается и является доступной в новом развертывании Nano Server для Windows Server2016. |
| [Поддержка упрощенного резервного копирования](data-deduplication/whats-new.md#simple-backup-support) | Создать | Поддержка виртуализированных приложений резервного копирования (например, [Microsoft Data Protection Manager](https://technet.microsoft.com/en-us/library/hh758173.aspx)) в Windows Server2012R2 реализовывалась в ходе многоэтапной настройки вручную. В Windows Server2016 представлен новый стандартный тип использования ("Резервная копия"), обеспечивающий при непрерывное развертывание дедупликации данных для виртуализированных приложений резервного копирования. |
| [Поддержка последовательных обновлений кластерной ОС](data-deduplication/whats-new.md#cluster-upgrade-support) | Создать | Дедупликация данных полностью поддерживает новую функцию [последовательного обновления кластерной ОС](..//failover-clustering/cluster-operating-system-rolling-upgrade.md) в Windows Server2016. |

## <a name="smb-hardening-improvements"></a>Усиление защиты SMB для подключения к ресурсам SYSVOL и NETLOGON  
В Windows10 и Windows Server2016 для клиентских подключений по умолчанию к общим папкам SYSVOL и NETLOGON на контроллерах домена в доменных службах Active Directory теперь требуется подписывание SMB-пакетов и взаимная проверка подлинности (например, Kerberos).   

**Какой эффект дает это изменение?**  
Это изменение снижает вероятность атак типа "человек посередине".   

**Что работает иначе?**  
При отсутствии подписи SMB и взаимной проверки подлинности компьютер под управлением Windows10 или Windows Server2016 не сможет обрабатывать групповую политику и скрипты доменных устройств.  

> [!NOTE]  
> Значения реестра по умолчанию для этих настроек отсутствуют, но правила усиления защиты применяются, пока не будут переопределены групповой политикой или другими значениями реестра.  

Дополнительные сведения об усовершенствованиях системы безопасности (усилению защиты UNC) см. в статье [3000483](http://support.microsoft.com/kb/3000483) базы знаний Майкрософт, а также в статье об усилении защиты групповых политик [MS15-011 & MS15-014: Hardening Group Policy](http://blogs.technet.microsoft.com/srd/2015/02/10/ms15-011-ms15-014-hardening-group-policy).  

## <a name="work-folders"></a>рабочие папки
Улучшено уведомление об изменениях, если сервер рабочих папок работает под управлением Windows Server2016, а клиент рабочих папок— под управлением Windows10.

**Какой эффект дает это изменение?**<br>
При использовании Windows Server2012R2, если изменения файлов синхронизируются с сервером рабочих папок, клиенты не получают уведомления об изменениях и ожидают обновления 10минут.  При использовании Windows Sever2016 сервер рабочих папок мгновенно оповещает клиенты Windows10, и изменения в файлах синхронизируются немедленно.

**Что работает иначе?**<br>
Это новая функция в Windows Server2016. Для нее требуется сервер рабочих папок с ОС Windows Server2016 и клиенты с ОС Windows 10.

Если вы используете клиент более ранней версии или сервер рабочих папок с ОС Windows Server2012R2, клиент будет по-прежнему производить опрос для проверки наличия изменений каждые десятьминут.

## <a name="refs"></a>ReFS 
Следующая итерация ReFS поддерживает развертывание крупномасштабных хранилищ с различными рабочими нагрузками, обеспечивая надежность, устойчивость и масштабируемость данных.     

**Какой эффект дает это изменение?**<br>
В ReFS имеются следующие улучшения:

* ReFS реализует новые функциональные возможности уровней хранилищ, что обеспечивает повышение производительности и емкости хранения. Эти новые функциональные возможности обеспечивают:
    * несколько типов устойчивости на одном виртуальном диске (например, с помощью зеркалирования на уровне производительности и четности на уровне емкости);
    * повышенную скорость реагирования на изменение рабочих наборов; 
    * поддержку носителей SMR (Shingled Magnetic Recording); 
* Применение технологии клонирования блоков значительно повышает производительность операций виртуальных машин, таких как операции слияния контрольных точек .vhdx.
* Новое средство сканирования ReFS позволяет выполнять восстановление хранилищ с утечками и помогает восстанавливать данные в случае серьезного их повреждения. 

**Что работает иначе?**<br>
Эти возможности впервые появились в Windows Server 2016. 

## <a name="see-also"></a>См. также  
* [Новые возможности Windows Server2016](../get-started/what-s-new-in-windows-server-2016.md)  