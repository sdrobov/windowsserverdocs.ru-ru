---
title: Виртуализация
description: В этой статье представлен обзор технологий виртуализации, таких как контейнеры, Hyper-V и виртуальный коммутатор Hyper-V, а также размещены ссылки на дополнительные ресурсы для Windows Server 2016 и более поздние версии операционной системы.
ms.prod: windows-server
manager: dougkim
ms.technology: compute
ms.topic: article
author: shortpatti
ms.author: pashort
ms.localizationpriority: medium
ms.date: 03/16/2018
ms.openlocfilehash: bbbd8ea812a25b0d538dcb87a380184412235b99
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71364045"
---
# <a name="virtualization"></a>Виртуализация

>Область применения. Windows Server (Semi-Annual Channel), Windows Server 2016 

>[!TIP]
> Ищете дополнительные сведения о старых версиях Windows Server? Ознакомьтесь с другими нашими [библиотеками Windows Server](/previous-versions/windows/) на сайте docs.microsoft.com. Кроме того, вы можете найти нужную информацию [на этом сайте](https://docs.microsoft.com/search/index?search=Windows+Server&dataSource=previousVersions).

<img src="../media/landing-icons/virtualization.png" style='float:left; padding:.5em;' alt="Icon showing a box with spokes"> Виртуализация в Windows Server 2016 — одна из базовых технологий, необходимых для создания программно-определяемой инфраструктуры. Вместе с сетью и хранилищем функции виртуализации предоставляют гибкость, необходимую для поддержки рабочих нагрузок ваших клиентов.

В число технологий виртуализации Windows Server входят обновления Hyper-V, виртуального коммутатора Hyper-V и защищенной структуры и экранированных виртуальных машин \(VMs @ no__t-1, что повышает безопасность, масштабируемость и надежность. Благодаря обновлениям отказоустойчивой кластеризации, сетевых компонентов и хранилища эти технологии еще удобнее развертывать и администрировать при использовании в сочетании с Hyper-V. 


<ul class="cardsI panelContent">
<li>
        <a href="../security/guarded-fabric-shielded-vm/guarded-fabric-and-shielded-vms-top-node.md">
          <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-access.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Защищенная структура и экранированные виртуальные машины</h3>
                        <p>Поставщики облачных служб и администраторы корпоративного частного облака могут использовать защищенную структуру для создания более безопасной среды для виртуальных машин. Защищенная структура состоит из одной службы защиты узла (HGS), которая обычно представлена кластером из трех узлов, одним или несколькими защищенными узлами и набором экранированных виртуальных машин.</p>
                    </div>
                </div>
            </div>
        </div>
       </a>
    </li>
<li>
        <a href="/hyper-v/Hyper-V-on-Windows-Server.md">
          <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-access.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Windows 10 для предприятия: способы использования устройств для работы</h3>
                        <p>Технология Hyper-V предоставляет вычислительные ресурсы с помощью виртуализации оборудования. Hyper-V создает программную версию компьютера, которую называют виртуальной машиной. Она используется для запуска операционной системы и приложений. Вы можете одновременно запускать несколько виртуальных машин, а также создавать и удалять их по мере необходимости. </p>
                    </div>
                </div>
            </div>
        </div>
       </a>
     </li>

<li>
        <a href="https://docs.microsoft.com/windows-server/virtualization/hyper-v/hyper-v-server-2016">
          <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-access.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Microsoft Hyper-V Server</h3>
                        <p>Технология Hyper-V предоставляет вычислительные ресурсы с помощью виртуализации оборудования. Hyper-V создает программную версию компьютера, которую называют виртуальной машиной. Она используется для запуска операционной системы и приложений. Вы можете одновременно запускать несколько виртуальных машин, а также создавать и удалять их по мере необходимости. </p>
                    </div>
                </div>
            </div>
        </div>
       </a>
     </li>


<li>
        <a href="hyper-v-virtual-switch/Hyper-V-Virtual-Switch.md">
          <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-access.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Виртуальный коммутатор Hyper-V</h3>
                        <p>Виртуальный коммутатор Hyper-V — это программный сетевой коммутатор Ethernet уровня 2, который доступен во всех версиях Hyper-V.</p>

                        <p>Виртуальный коммутатор Hyper-V доступен в диспетчере Hyper-V после установки роли сервера Hyper-V.</p>

                        <p>Виртуальный коммутатор Hyper-V предоставляет программно управляемые и расширяемые возможности для подключения виртуальных машин к виртуальным сетям и к физической сети.</p> 

                        <p>Виртуальный коммутатор Hyper-V также обеспечивает применение политик в области безопасности, изоляции и уровней обслуживания.</p>
                    </div>
                </div>
            </div>
        </div>
       </a>
     </li>


<li>
       <a href="https://docs.microsoft.com/virtualization/windowscontainers">
          <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-access.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Контейнеры Windows</h3>
                        <p>Контейнеры Windows обеспечивают виртуализацию на уровне операционной системы. Они позволяют запускать несколько изолированных приложений в одной системе. В этот компонент включены два разных типа среды выполнения контейнера, каждый из которых имеет разную степень изоляции приложения.</p>
                    </div>
                </div>
            </div>
        </div>
       </a>
     </li>




## <a name="related"></a>Статьи по теме

Для создания среды виртуализации платформе Hyper-V требуется специальное оборудование. Дополнительные сведения см. в разделе [Требования к системе для Hyper-V в Windows Server 2016](./hyper-v/system-requirements-for-hyper-v-on-windows.md). 

Дополнительные сведения см. в разделе [Hyper-V в Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows).

