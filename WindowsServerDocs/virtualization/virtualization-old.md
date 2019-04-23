---
title: Виртуализация
description: В этой статье представлен обзор технологий виртуализации, таких как контейнеры, Hyper-V и виртуальный коммутатор Hyper-V, а также размещены ссылки на дополнительные ресурсы для Windows Server 2016 и более поздние версии операционной системы.
ms.prod: windows-server-threshold
manager: dougkim
ms.technology: compute
ms.topic: article
author: shortpatti
ms.author: pashort
ms.localizationpriority: medium
ms.date: 03/16/2018
ms.openlocfilehash: b3b018037d788d47fafe7d3adda50cfb5831ab56
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59829915"
---
# <a name="virtualization"></a>Виртуализация

>Область применения. Windows Server (полугодовой канал), Windows Server 2016 

>[!TIP]
> Ищете дополнительные сведения о старых версиях Windows Server? Ознакомьтесь с нашими другими [библиотеками Windows Server](/previous-versions/windows/) на docs.microsoft.com. Кроме того, вы можете найти нужную информацию [на этом сайте](https://docs.microsoft.com/search/index?search=Windows+Server&dataSource=previousVersions).

<img src="../media/landing-icons/virtualization.png" style='float:left; padding:.5em;' alt="Icon showing a box with spokes"> Виртуализация в Windows Server 2016 — одна из базовых технологий, необходимых для создания программно-определяемой инфраструктуры. Вместе с сетью и хранилищем функции виртуализации предоставляют гибкость, необходимую для поддержки рабочих нагрузок ваших клиентов.

Технологии виртуализации Windows Server включают обновления Hyper-V, виртуальный коммутатор Hyper-V и Защищенная структура и экранированные виртуальные машины \(виртуальных машин\), который повышает безопасность, масштабируемость и надежность. Благодаря обновлениям отказоустойчивой кластеризации, сетевых компонентов и хранилища эти технологии еще удобнее развертывать и администрировать при использовании в сочетании с Hyper-V. 


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
                        <p>Поставщики облачных услуг и администраторы корпоративного частного облака могут использовать защищенную структуру для создания более безопасной среды для виртуальных машин. Защищенная структура состоит из одной службы защиты узла \(HGS\) -как правило, кластер из трех узлов -, а также один или несколько защищенных узлов и набора экранированных виртуальных машин.</p>
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
                        <h3>Windows 10 для предприятия: Использование устройств для работы</h3>
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
                        <p>Hyper\-виртуальный коммутатор V — это программное обеспечение\-основе слой\-2 сетевой коммутатор Ethernet, который включается во все версии Hyper\-V.</p>

                        <p>Hyper\-V виртуальный коммутатор доступен в Hyper\-V Manager после установки Hyper\-V роли сервера.</p>

                        <p>Включенные в Hyper\-V виртуального коммутатора, программно управляемые и расширяемые возможности, которые дают возможность подключения виртуальных машин к виртуальным сетям и физической сети.</p> 

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
                        <p>Контейнеры Windows предоставляют операционную систему\-виртуализацию на уровне, которая позволяет нескольким приложениям, изолированной для запуска на одном компьютере. В этот компонент включены два разных типа среды выполнения контейнера, каждый из которых имеет разную степень изоляции приложения.</p>
                    </div>
                </div>
            </div>
        </div>
       </a>
     </li>




## <a name="related"></a>Статьи по теме

Для создания среды виртуализации платформе Hyper-V требуется специальное оборудование. Дополнительные сведения см. в разделе [Требования к системе для Hyper-V в Windows Server 2016](./hyper-v/system-requirements-for-hyper-v-on-windows.md). 

Дополнительные сведения см. в разделе [Hyper-V в Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows).

