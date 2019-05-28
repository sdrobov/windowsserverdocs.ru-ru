---
ms.assetid: c9844427-27cf-4d76-b5bb-e06368b092f7
title: Отказоустойчивая кластеризация
ms.prod: windows-server-threshold
layout: LandingPage
ms.topic: landing-page
ms.manager: dongill
author: JasonGerend
ms.author: jgerend
ms.technology: storage-failover-clustering
ms.date: 03/08/2019
ms.localizationpriority: high
ms.openlocfilehash: 9e4184e52ef48e758ebc80e63d3d6f952a09cc2c
ms.sourcegitcommit: 8ba2c4de3bafa487a46c13c40e4a488bf95b6c33
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/25/2019
ms.locfileid: "66222456"
---
# <a name="failover-clustering-in-windows-server"></a>Отказоустойчивая кластеризация в Windows Server

> Относится к: Windows Server 2019, Windows Server 2016

>[!TIP]
> Ищете дополнительные сведения о старых версиях Windows Server? Ознакомьтесь с другими нашими [библиотеками Windows Server](/previous-versions/windows/) на сайте docs.microsoft.com. Кроме того, вы можете найти нужную информацию [на этом сайте](https://docs.microsoft.com/search/index?search=Windows+Server&dataSource=previousVersions).

<hr />

Отказоустойчивый кластер — это группа независимых компьютеров, которые работают совместно в целях повышения доступности и масштабируемости кластерных ролей (ранее называемых кластерными приложениями и службами). Кластерные серверы (называемые "узлы") соединены физическими кабелями и программным обеспечением. При сбое на одном из узлов кластера его функции немедленно передаются другим узлам (этот процесс называется отработкой отказа). Кроме того, за кластерными ролями ведется профилактическое наблюдение, чтобы обеспечить их правильную работу. Если они не работают, выполняется перезагрузка или перемещение на другой узел.

Отказоустойчивые кластеры также предоставляют функции общего тома кластера (CSV), которые образуют согласованное распределенное пространство имен, используемое кластерными ролями для доступа к общему хранилищу со всех узлов. Благодаря функции отказоустойчивой кластеризации пользователи сталкиваются с минимальным количеством проблем в работе службы.

Отказоустойчивая кластеризация имеет много вариантов практического применения, такие как:
* Высокодоступное или постоянно доступное хранилище файловых ресурсов общего доступа для приложений, таких как Microsoft SQL Server и виртуальные машины Hyper-V.
* Высокодоступные кластерные роли, выполняемые на физических серверах или виртуальных машинах, установленных на серверах, на которых выполняется Hyper-V.


|  |  |
|---------|---------|
|![Что нового](../media/i-whats-new.svg)  | [**Новые возможности отказоустойчивой кластеризации**](whats-new-in-failover-clustering.md) |


|  |  |  |
|---------|---------|---------|
|![Понять](../media/i-cluster.svg)**понять**  |  ![Планирование](../media/i-cluster.svg)**планирования**  |  ![Развертывание](../media/i-cluster.svg)**развертывания**       |
| [Масштабируемый файловый сервер для данных приложений](sofs-overview.md)    |   [Планирование оборудования требования к отказоустойчивой кластеризации и варианты хранилища](clustering-requirements.md)      |  [Развертывание Предварительная подготовка кластеризованных объектов-компьютеров в доменных службах Active Directory](prestage-cluster-adds.md)  |
|  [Кворум кластеров и пулов](../storage/storage-spaces/understand-quorum.md)   |   [Использование общих томов кластера (CSV)](failover-cluster-csvs.md)      | [Создание отказоустойчивого кластера](create-failover-cluster.md)        |
|  [Служба сведений о домене сбоя](fault-domains.md)   |  [С помощью кластеров гостевых виртуальных машин с дисковыми пространствами](../storage/storage-spaces/storage-spaces-direct-in-vm.md)       | [Развертывание двухузлового файлового сервера](../storage/storage-spaces/storage-spaces-direct-in-vm.md)        |
| [Упрощенные сети кластера SMB Multichannel и Multi-NIC](smb-multichannel.md)    |         |  [Управление кворума и свидетеля](manage-cluster-quorum.md)       |
|   [Балансировка нагрузки для виртуальных машин](vm-load-balancing-overview.md)  |         |   [Развертывание облака-свидетеля](deploy-cloud-witness.md)      |
|   [Наборы кластеров](../storage/storage-spaces/cluster-sets.md)  |         |     [Развертывание файлового ресурса-свидетеля](file-share-witness.md)    |
|   [Сходство кластеров](cluster-affinity.md)  |         |    [Последовательное обновление ОС кластера]()     |
|     |         |     [Обновление отказоустойчивого кластера на одном оборудовании](upgrade-option-same-hardware.md)    |
|     |         |     [Развертывание кластера отсоединенных Active Directory](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265970\(v%3dws.11\))    |


|  |  |  |
|---------|---------|---------|
|![Управление](../media/i-cluster.svg)**управление**  |  ![Средства и параметры](../media/i-cluster.svg)**средства и параметры**  |  ![Ресурсы сообщества](../media/i-cluster.svg)**ресурсы сообщества**       |
| [Кластерное обновление](cluster-aware-updating.md)    |   [Командлеты отказоустойчивой кластеризации PowerShell](https://docs.microsoft.com/powershell/module/failoverclusters/?view=win10-ps)      |  [Форум по высокой доступности (кластеризации)](https://go.microsoft.com/fwlink/p/?LinkId=230641)       |
|  [Служба работоспособности](health-service-overview.md)   |   [Учитывать командлеты PowerShell для обновления кластера](https://docs.microsoft.com/powershell/module/clusterawareupdating/?view=win10-ps)      | [Отказоустойчивая кластеризация и сети блог группы балансировки нагрузки](http://blogs.msdn.com/b/clustering/)        |
|  [Перенос кластера между доменами](cluster-domain-migration.md)   |         |         |
|  [Устранение неполадок с помощью отчетов об ошибках Windows](troubleshooting-using-wer-reports.md)   |         |         |
