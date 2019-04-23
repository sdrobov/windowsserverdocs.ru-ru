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
ms.openlocfilehash: 445de065ff5b68b83481ee5bd83ebf18fdd180a7
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59848655"
---
# <a name="failover-clustering-in-windows-server"></a>Отказоустойчивая кластеризация в Windows Server

> Относится к: Windows Server 2019 г., Windows Server 2016, Windows Server (Semi-Annual Channel)

>[!TIP]
> Ищете дополнительные сведения о старых версиях Windows Server? Ознакомьтесь с нашими другими [библиотеками Windows Server](/previous-versions/windows/) на docs.microsoft.com. Кроме того, вы можете найти нужную информацию [на этом сайте](https://docs.microsoft.com/search/index?search=Windows+Server&dataSource=previousVersions).

<hr />

Отказоустойчивый кластер — это группа независимых компьютеров, которые работают совместно в целях повышения доступности и масштабируемости кластерных ролей (ранее называемых кластерными приложениями и службами). Кластерные серверы (называемые "узлы") соединены физическими кабелями и программным обеспечением. При сбое на одном из узлов кластера его функции немедленно передаются другим узлам (этот процесс называется отработкой отказа). Кроме того, за кластерными ролями ведется профилактическое наблюдение, чтобы обеспечить их правильную работу. Если они не работают, выполняется перезагрузка или перемещение на другой узел.

Отказоустойчивые кластеры также предоставляют функции общего тома кластера (CSV), которые образуют согласованное распределенное пространство имен, используемое кластерными ролями для доступа к общему хранилищу со всех узлов. Благодаря функции отказоустойчивой кластеризации пользователи сталкиваются с минимальным количеством проблем в работе службы.

Отказоустойчивая кластеризация имеет много вариантов практического применения, такие как:
* Высокодоступное или постоянно доступное хранилище файловых ресурсов общего доступа для приложений, таких как Microsoft SQL Server и виртуальные машины Hyper-V.
* Высокодоступные кластерные роли, выполняемые на физических серверах или виртуальных машинах, установленных на серверах, на которых выполняется Hyper-V.

<hr />

<ul class="cardsF panelContent">
<li>
                         <div class="cardSize">
                                <div class="cardPadding">
                                    <div class="card">
                                        <div class="cardImageOuter">
                                            <div class="cardImage">
                                                <img src="../media/i-whats-new.svg" alt="" />
                                            </div>
                                        </div>
                                        <div class="cardText">
                                        <h2><a href="whats-new-in-failover-clustering.md">Новые возможности отказоустойчивой кластеризации</a></h2>
                                        </div>
                                    </div>
                                </div>
                             </div>
                          </a>
                        </li>
                     </ul>
<HR />

<ul class="cardsF panelContent">

<li>
                         <div class="cardSize">
                                <div class="cardPadding">
                                    <div class="card">
                                        <div class="cardImageOuter">
                                            <div class="cardImage">
                                                <img src="../media/i-cluster.svg" alt="" />
                                            </div>
                                        </div>
                                        <div class="cardText">
                                        <h3>Общие сведения</h3>
<HR />
                                        <p><a href="sofs-overview.md">Масштабируемого файлового сервера для данных приложений</a></p>
<HR />
                                        <p><a href="../storage/storage-spaces/understand-quorum.md">Кворум кластера и пула</a></p>
<HR />
                                        <p><a href="fault-domains.md">Информация о домене сбоя</a></p>
<HR />
                                        <p><a href="smb-multichannel.md">Упрощенное сетей кластера для SMB Multichannel и multi-NIC</a></p>
<HR />
                                        <p><a href="vm-load-balancing-overview.md">Балансировка нагрузки для виртуальных Машин</a></p>
<HR />
                                        <p><a href="../storage/storage-spaces/cluster-sets.md">Наборы кластера</a></p>
<HR />
                                        <p><a href="cluster-affinity.md">Сходство кластера</a></p>
                                        </div>
                                    </div>
                                </div>
                            </div>
                          </a>
                        </li>

<li>
                         <div class="cardSize">
                                <div class="cardPadding">
                                    <div class="card">
                                        <div class="cardImageOuter">
                                            <div class="cardImage">
                                                <img src="../media/i-cluster.svg" alt="" />
                                            </div>
                                        </div>
                                        <div class="cardText">
                                        <h3>Планирование</h3>
<HR />
                                        <p><a href="clustering-requirements.md">FailOver Clustering Hardware Requirements и варианты хранилища</a></p>
<HR />
                                        <p><a href="failover-cluster-csvs.md">Использование общих томов (CSV) кластера</a></p>               
<HR />
                                        <p><a href="../storage/storage-spaces/storage-spaces-direct-in-vm.md">С помощью кластеров гостевых виртуальных машин с дисковыми пространствами</a></p>
                                        </div>
                                    </div>
                                </div>
                            </div>
                          </a>
                        </li>
<li>
                         <div class="cardSize">
                                <div class="cardPadding">
                                    <div class="card">
                                        <div class="cardImageOuter">
                                            <div class="cardImage">
                                                <img src="../media/i-cluster.svg" alt="" />
                                            </div>
                                        </div>
                                        <div class="cardText">
                                        <h3>Развертывание</a></h3> 
<HR />
                                        <p><a href="prestage-cluster-adds.md">Предварительная подготовка кластеризованных объектов-компьютеров в доменных службах Active Directory</a></p>
<HR />
                                        <p><a href="create-failover-cluster.md">Создание отказоустойчивого кластера</a></p> 
<HR />
                                        <p><a href="deploy-two-node-clustered-file-server.md">Развертывание двухузлового файлового сервера</a></p> 
<HR />
                                        <p><a href="manage-cluster-quorum.md">Управление кворума и свидетеля</a></p> 
<HR />
                                        <p><a href="deploy-cloud-witness.md">Развертывание облака-свидетеля</a></p>
<HR />
                                        <p><a href="file-share-witness.md">Развертывание файлового ресурса-свидетеля</a></p>
<HR />
                                        <p><a href="cluster-operating-system-rolling-upgrade.md">Последовательные обновления ОС кластера</a></p> 
<HR />
                                        <p><a href="upgrade-option-same-hardware.md">Обновление отказоустойчивого кластера на одном оборудовании</a></p>
<HR />
                                        <p><a href="https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265970\(v%3dws.11\)">Развертывание кластера отсоединенных Active Directory</a></p>
                                        </div>
                                    </div>
                                </div>
                            </div>
                          </a>
                        </li>
                     </ul>
<HR />
<ul class="cardsF panelContent">
<li>
                         <div class="cardSize">
                                <div class="cardPadding">
                                    <div class="card">
                                        <div class="cardImageOuter">
                                            <div class="cardImage">
                                                <img src="../media/i-cluster.svg" alt="" />
                                            </div>
                                        </div>
                                        <div class="cardText">
                                        <h3>Управление</h3>
<HR />
                                        <p><a href="cluster-aware-updating.md">Кластерное обновление</a></p> 
<HR />
                                        <p><a href="health-service-overview.md">Служба работоспособности</a></p>
<HR />
                                        <p><a href="cluster-domain-migration.md">Домен кластера миграции</a></p>
<HR />
                                        <p><a href="troubleshooting-using-wer-reports.md">Устранение неполадок с помощью отчетов об ошибках Windows</a></p> 
                                        </div>
                                    </div>
                                </div>
                            </div>
                          </a>
                        </li>
<li>
                         <div class="cardSize">
                                <div class="cardPadding">
                                    <div class="card">
                                        <div class="cardImageOuter">
                                            <div class="cardImage">
                                                <img src="../media/i-cluster.svg" alt="" />
                                            </div>
                                        </div>
                                        <div class="cardText">
                                        <h3>Средства и параметры</a></h3>
<HR />
                                        <p><a href="https://docs.microsoft.com/powershell/module/failoverclusters/?view=win10-ps">Командлеты отказоустойчивой кластеризации PowerShell</a></p> 
<HR />
                                        <p><a href="https://docs.microsoft.com/powershell/module/clusterawareupdating/?view=win10-ps">Учитывать командлеты PowerShell для обновления кластера</a></p> 
                                        </div>
                                    </div>
                                </div>
                            </div>
                          </a>
                        </li>
<li>
                         <div class="cardSize">
                                <div class="cardPadding">
                                    <div class="card">
                                        <div class="cardImageOuter">
                                            <div class="cardImage">
                                                <img src="../media/i-cluster.svg" alt="" />
                                            </div>
                                        </div>
                                        <div class="cardText">
                                        <h3>Ресурсы сообщества</a></h3>
<HR />
                                        <p><a href="https://go.microsoft.com/fwlink/p/?LinkId=230641">Форум по высокой доступности (кластеризации)</a></p> 
<HR />
                                        <p><a href="http://blogs.msdn.com/b/clustering/">Отказоустойчивая кластеризация и сети блог группы балансировки нагрузки</a></p> 
                                        </div>
                                    </div>
                                </div>
                            </div>
                          </a>
                        </li>
</ul>
