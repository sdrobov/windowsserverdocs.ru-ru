---
title: Изучение и просмотр повторной синхронизации хранилища
description: Подробные сведения о том, когда происходит повторная синхронизация хранилища и как она отображается в Windows Server 2019.
ms.prod: windows-server
ms.author: adagashe
ms.technology: storage-spaces
ms.topic: article
author: adagashe
ms.date: 01/14/2019
ms.localizationpriority: medium
ms.openlocfilehash: 79e5e1e9daba005a086c16dd1d8e3e3f9a28a8a2
ms.sourcegitcommit: 771db070a3a924c8265944e21bf9bd85350dd93c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2020
ms.locfileid: "85473421"
---
# <a name="understand-and-monitor-storage-resync"></a>Принцип работы и отслеживание повторной синхронизации хранилища

>Область применения: Windows Server 2019

Оповещения о повторной синхронизации хранилища — это новая возможность [Локальные дисковые пространства](storage-spaces-direct-overview.md) в Windows Server 2019, которая позволяет служба работоспособности вызывать ошибку при повторной синхронизации хранилища. Оповещение полезно при уведомлении о том, что происходит повторная синхронизация, чтобы вы не затронули больше серверов (что может привести к появлению нескольких доменов сбоя, в результате чего кластер будет отключен).

В этом разделе приводятся общие сведения и действия для понимания и просмотра повторной синхронизации хранилища в отказоустойчивом кластере Windows Server с Локальные дисковые пространства.

## <a name="understanding-resync"></a>Основные сведения о повторной синхронизации

Начнем с простого примера, чтобы понять, как хранилище становится несинхронизированным. Следует помнить, что такое поведение характерно для всех общих дисков (только на локальных дисках). Как можно увидеть ниже, если один Серверный узел выйдет из строя, то его диски не будут обновлены до тех пор, пока не вернется в режим «в сети». это справедливо для любой архитектуры с согласованием Hyper-in.

Предположим, что мы хотим сохранить строку "HELLO".

![ASCII строки "Hello"](media/understand-storage-resync/hello.png)

Асссуминг, что у нас есть три способа обеспечения отказоустойчивости зеркала, у нас есть три копии этой строки. Теперь, если мы временно перестали использовать сервер #1 (для маинтаненце), мы не можем получить доступ к #1 копирования.

![Не удается получить доступ к #1 копирования](media/understand-storage-resync/copy1.png)

Предположим, что мы обновляем нашу строку с "HELLO" на "HELP!" в настоящее время.

![ASCII строки "Help!"](media/understand-storage-resync/help.png)

После обновления строки Copy #2 и #3 будут успешно обновлены. Однако копирование #1 по-прежнему недоступно, так как сервер #1 временно отключен (для маинтаненце).

![GIF записи для копирования #2 и #2 "](media/understand-storage-resync/write.gif)

Теперь у нас есть копия #1 с данными, которые не синхронизированы. Операционная система использует детализированное отслеживание "грязного" региона для отслеживания несинхронизированных битов. Таким образом, когда сервер #1 возвращается в режим «в сети», можно синхронизировать изменения, считывая данные из #2 копирования или #3 и перезаписав данные в #1 копирования. Преимуществом этого подхода является то, что нам нужно только скопировать устаревшие данные вместо повторной синхронизации всех данных с сервера #2 или сервера #3.

![GIF перезаписи для копирования #1 "](media/understand-storage-resync/overwrite.gif)

Таким образом, объясняется, как данные выходят из синхронизации. Но как это выглядит на высоком уровне? Предположим, что в этом примере имеется три сервера кластера Hyper-in. Когда сервер #1 находится в состоянии обслуживания, вы увидите, что он не работает. При переводе сервера #1 резервной копии запускается повторная синхронизация всех его хранилищ с помощью детального отслеживания "грязного" региона (см. описание выше). После синхронизации данных все серверы будут отображаться как включенные.

![GIF-файл административного представления повторной синхронизации "](media/understand-storage-resync/admin.gif)

## <a name="how-to-monitor-storage-resync-in-windows-server-2019"></a>Мониторинг повторной синхронизации хранилища в Windows Server 2019

Теперь, когда вы понимаете, как работает повторная синхронизация хранилища, давайте посмотрим, как это видно в Windows Server 2019. Мы добавили новую ошибку в [Служба работоспособности](../../failover-clustering/health-service-overview.md) , которая будет отображаться при повторной синхронизации хранилища.

Чтобы просмотреть эту ошибку в PowerShell, выполните следующую команду:

``` PowerShell
Get-HealthFault
```

Это новая ошибка в Windows Server 2019, которая появится в PowerShell, в отчете о проверке кластера и в любом другом месте, где происходит сбой.

Чтобы получить более глубокое представление, можно запросить базу данных временных рядов в PowerShell следующим образом:

```PowerShell
Get-ClusterNode | Get-ClusterPerf -ClusterNodeSeriesName ClusterNode.Storage.Degraded
```
Вот пример выходных данных:

```
Object Description: ClusterNode Server1

Series                       Time                Value Unit
------                       ----                ----- ----
ClusterNode.Storage.Degraded 01/11/2019 16:26:48     214 GB
```

В частности, центр администрирования Windows использует сбои работоспособности для задания состояния и цвета узлов кластера. Таким образом, эта новая ошибка приведет к тому, что узлы кластера будут переходить с красного (вниз) на желтый (повторная синхронизация) в зеленый (вверх), а не с красного на зеленый на панели мониторинга ХЦИ.

![Изображение представления о повторной синхронизации для 2016 и 2019 "](media/understand-storage-resync/compare.png)

Показывая общий ход выполнения повторной синхронизации хранилища, можно точно определить, какой объем данных не синхронизирован, а также о том, выполняется ли пересылка системы. При открытии центра администрирования Windows и переходе на *панель мониторинга*вы увидите новое оповещение следующим образом:

![Изображение оповещения в центре администрирования Windows](media/understand-storage-resync/alert.png)

Оповещение полезно при уведомлении о том, что происходит повторная синхронизация, чтобы вы не затронули больше серверов (что может привести к появлению нескольких доменов сбоя, в результате чего кластер будет отключен).

Если перейти на страницу *серверы* в центре администрирования Windows, щелкнуть *Инвентаризация*, а затем выбрать конкретный сервер, можно получить более подробное представление о том, как эта повторная синхронизация хранилища будет просматриваться отдельно для каждого сервера. Если вы перейдете на сервер и посмотрите на диаграмму *хранилища* , то увидите объем данных, которые необходимо исправить, в *фиолетовой* строке с точным числом справа. Это значение увеличится при отключении сервера (больше данных необходимо повторно синхронизировать) и постепенно снизится после возвращения сервера в режим «в сети» (синхронизация данных). Когда объем данных, требующих восстановления, равен 0, выполняется повторная синхронизация хранилища. Теперь вы можете отключить сервер при необходимости. Ниже приведен снимок экрана с этим интерфейсом в центре администрирования Windows.

![Изображение представления "сервер" в центре администрирования Windows "](media/understand-storage-resync/server.png)

## <a name="how-to-see-storage-resync-in-windows-server-2016"></a>Как увидеть повторную синхронизацию хранилища в Windows Server 2016

Как видите, это предупреждение особенно полезно для получения целостного представления о том, что происходит на уровне хранилища. Он эффективно суммирует сведения, которые можно получить из командлета Get-Сторажежоб, который возвращает сведения о длительных заданиях модуля хранилища, таких как операция восстановления в дисковом пространстве. Пример приведен ниже.

```PowerShell
Get-StorageJob
```

Ниже приведен пример выходных данных:

```
Name                  ElapsedTime           JobState              PercentComplete       IsBackgroundTask
----                  -----------           --------              ---------------       ----------------
Regeneration          00:01:19              Running               50                    True

```

Это представление гораздо более детализировано, так как задания хранилища в списке относятся к тому, вы видите список выполняемых заданий и можете отслеживать их отдельный ход выполнения. Этот командлет работает как с Windows Server 2016, так и с 2019.

## <a name="additional-references"></a>Дополнительные ссылки

- [Перевод сервера в автономный режим для обслуживания](maintain-servers.md)
- [Обзор Локальные дисковые пространства](storage-spaces-direct-overview.md)