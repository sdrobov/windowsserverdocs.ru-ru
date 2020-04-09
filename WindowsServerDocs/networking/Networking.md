---
title: Сеть
description: В этом разделе представлен обзор технологий программно-конфигурируемой сети и сетевой платформы, которые доступны в Windows Server 2016.
ms.prod: windows-server
layout: LandingPage
ms.technology: networking
ms.topic: landing-page
ms.assetid: daaf6b61-5953-4c2d-b6b8-7c885b552646
manager: dougkim
ms.author: anpaul
author: AnirbanPaul
ms.localizationpriority: medium
ms.openlocfilehash: de1acf0a0ed233fdd7675da3bca63f7f16824a9a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80855807"
---
# <a name="networking"></a>Сеть

>[!TIP]
> Ищете дополнительные сведения о старых версиях Windows Server? Ознакомьтесь с другими нашими [библиотеками Windows Server](/previous-versions/windows/) на сайте docs.microsoft.com. Кроме того, вы можете найти нужную информацию [на этом сайте](https://docs.microsoft.com/search/index?search=Windows+Server&dataSource=previousVersions).

<hr />

Сеть — это базовая часть программно определенного центра обработки данных \(SDDC\) Platform, и Windows Server 2016 предоставляет новые и улучшенные программно-определяемые сетевые \(технологии SDN\), которые помогут вам перейти к полностью реализованному решению SDDC для вашей организации.

При управлении сетями в качестве программно определенного ресурса можно описать требования к инфраструктуре приложения один раз, а затем выбрать, где приложение выполняется локально или в облаке. 

Такая согласованность упрощает масштабирование приложений и позволяет легко запускать их в любом месте с полной уверенностью в безопасности, производительности, качестве обслуживания и доступности.

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
                    <h2><a href="../networking/What-s-New-in-Networking.md">Новые&#39;возможности работы с сетью</a></h2>
                    </div>
                </div>
            </div>
        </div>
    </li>
</ul>

<hr />

<h2>Программно-конфигурируемая сеть</h2>

<ul class="cardsF panelContent">
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-network.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><a href="https://docs.microsoft.com/windows-server/networking/sdn/">Программно-конфигурируемая сеть (SDN)</a></h3>
                        <hr />
                        <p>Этот раздел поможет получить представление о технологиях программно-конфигурируемых сетей, входящих в состав Windows Server System Center и Microsoft Azure.</p>
                        <p><b>Примечание.</b> Для узлов Hyper-V и виртуальных машин, на которых выполняются серверы инфраструктуры SDN, такие как узлы сетевого контроллера и программной балансировки нагрузки, необходимо установить Windows Server Datacenter Edition. Для узлов Hyper-V, содержащих только виртуальные машины рабочей нагрузки клиента, подключенные к сетям, управляемым SDN, можно использовать Windows Server Standard Edition.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <hr />
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-network.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                    <h3><a href="sdn/deploy/Deploy-a-Software-Defined-Network-infrastructure-using-scripts.md">Развертывание программно-определяемой сетевой инфраструктуры с помощью сценариев</a></h3>
                    <hr />
                    <p>Это руководство содержит инструкции по развертыванию сетевого контроллера с виртуальными сетями и шлюзами в тестовой лабораторной среде.</p>
                </div>
                </div>
            </div>
        </div>
    </li>
    <hr />
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-network.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><a href="sdn/technologies/network-controller/Network-Controller.md">Сетевой контроллер</a></h3>
                        <hr />
                        <p>Сетевой контроллер обеспечивает централизованную программируемую точку автоматизации для управления, настройки, мониторинга, а также выявления и устранения неисправностей в виртуальной и физической сетевой инфраструктуре центра данных.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <hr />
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-network.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><a href="sdn/technologies/network-function-virtualization/software-load-balancing-for-sdn.md">Подсистема &#40;балансировки&#41; нагрузки ПРОГРАММного обеспечения для Sdn</a></h3>
                        <hr />
                        <p>Поставщики облачных служб (CSP) и предприятия, которые развертывают программно-определяемую сеть (SDN) в Windows Server 2016, могут использовать программную балансировку нагрузки (SLB) для равномерного распределения сетевого трафика клиентов клиента и клиента между ресурсами виртуальной сети. Windows Server SLB позволяет размещать одну и ту же рабочую нагрузку на нескольких серверах, что обеспечивает высокий уровень доступности и масштабирование.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <hr />
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-network.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><a href="sdn/technologies/network-function-virtualization/RAS-Gateway-for-SDN.md">Шлюз RAS-сервера для SDN</a></h3>
                        <hr />
                        <p>Шлюз RAS, который является маршрутизатором, поддерживающим программное обеспечение, клиент протокол BGP (BGP) в Windows Server 2016, предназначен для поставщиков облачных служб (CSP) и предприятий, где размещаются виртуальные сети клиентов с помощью сети Hyper-V. Технология.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <hr />
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-network.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><a href="sdn/technologies/network-function-virtualization/Network-Function-Virtualization.md">Виртуализация сетевой функции</a></h3>
                        <hr />
                        <p>В программно определенных центрах обработки данных сетевые функции, выполняемые аппаратными устройствами (например, подсистемы балансировки нагрузки, брандмауэры, маршрутизаторы, коммутаторы и т. д.), все чаще виртуализованы как виртуальные устройства. Это &quot;&quot; виртуализации сетевых функций — это естественный прогресс виртуализации серверов и виртуализации сети.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <hr />
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-network.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><a href="sdn/technologies/network-function-virtualization/Datacenter-Firewall-Overview.md">Обзор брандмауэра центра обработки данных</a></h3>
                        <hr />
                        <p>Брандмауэр центра обработки данных —брандмауэр сетевого уровня с пятью кортежами (протокол, номера начального и конечного портов, начальный и конечный IP-адреса), с функцией отслеживания состояния и поддержкой нескольких клиентов.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
</ul>

<hr />

## <a name="networking-technologies"></a><a name="bkmk_networking"></a>Сетевые технологии

<ul class="cardsF panelContent">
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-network.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><a href="branchcache/BranchCache.md">BranchCache</a></h3>
                        <hr />
                        <p>BranchCache — это технология оптимизации пропускной способности глобальной сети (WAN). Для оптимизации пропускной способности глобальной сети служба BranchCache получает данные с серверов содержимого в главном офисе или облаке и помещает их в кэш на компьютерах филиала, когда пользователи получают доступ к содержимому на удаленных серверах, что позволяет обеспечить для клиентских компьютеров в филиалах локальный доступ к данным вместо доступа по глобальной сети.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <hr />
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-network.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><a href="core-network-guide/core-network-guide-windows-server.md">Основное сетевое руководством</a></h3>
                        <hr />
                        <p>Узнайте, как развернуть сеть Windows Server с помощью руководства по основной сети, а также добавить компоненты в сетевое развертывание с помощью вспомогательных руководств по основной сети.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <hr />
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-network.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><a href="../remote/remote-access/directaccess/DirectAccess.md">DirectAccess</a></h3>
                        <hr />
                        <p>DirectAccess предоставляет удаленным пользователям возможность подключения к сетевым ресурсам организации. </p>
                    </div>
                </div>
            </div>
        </div>
    </li>
   <hr />
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-network.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><a href="dns/dns-top.md">Служба доменных имен (DNS)</a></h3>
                        <hr />
                        <p>Служба доменных имен (DNS) — это один из стандартных отраслевых протоколов, включающих TCP/IP, а клиент DNS и DNS-сервер предоставляют службам разрешения имен IP-адресов компьютеров и пользователей.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <hr />
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-network.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><a href="technologies/dhcp/dhcp-top.md">DHCP протокол &#40;динамической настройки узла&#41;</a></h3>
                        <hr />
                        <p>Протокол DHCP — это протокол клиента или сервера, который автоматически предоставляет узел протокола IP с его IP-адресом и другие связанные сведения о конфигурации, такие как маска подсети и шлюз по умолчанию.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <hr />
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-network.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><a href="sdn/technologies/hyper-v-network-virtualization/Hyper-V-Network-Virtualization.md">Виртуализация сети Hyper-V</a></h3>
                        <hr />
                        <p>Виртуализация сети Hyper-V (HNV) обеспечивает виртуализацию сетей клиентов поверх общей инфраструктуры физической сети.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <hr />
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-network.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><a href="../virtualization/hyper-v-virtual-switch/Hyper-V-Virtual-Switch.md">Виртуальный коммутатор Hyper-V</a></h3>
                        <hr />
                        <p>Виртуальный коммутатор Hyper-V — это программный сетевой коммутатор Ethernet уровня 2, который доступен в диспетчере Hyper-V при установке роли сервера Hyper-V. Коммутатор предоставляет программно управляемые и расширяемые возможности для подключения виртуальных машин к виртуальным сетям и к физической сети. Виртуальный коммутатор Hyper-V также обеспечивает применение политик в области безопасности, изоляции и уровней обслуживания. </p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <hr />
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-network.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><a href="technologies/ipam/ipam-top.md">IPAM по управлению &#40;IP-адресами&#41;</a></h3>
                        <hr />
                        <p>Управление IP-адресами (IPAM) — это интегрированный набор средств для комплексного планирования, развертывания, управления и мониторинга инфраструктуры IP-адресов с богатым интерфейсом пользователя. IPAM автоматически определяет серверы инфраструктуры IP-адресов и DNS-серверы в вашей сети и позволяет управлять ими из центрального интерфейса.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <hr />
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-network.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><a href="technologies/Network-Load-Balancing.md">Балансировка сетевой нагрузки</a></h3>
                        <hr />
                        <p>Балансировка сетевой нагрузки (NLB) распределяет трафик между несколькими серверами с помощью сетевого протокола TCP/IP. Для развертываний, отличных от SDN, балансировка сетевой нагрузки гарантирует, что приложения без отслеживания состояния, такие как веб-серверы, работающие службы IIS (IIS), будут масштабироваться путем добавления дополнительных серверов при увеличении нагрузки.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <hr />
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-network.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><a href="technologies/hpn/hpn-top.md">Высокопроизводительные сети</a></h3>
                        <hr />
                        <p>К технологиям разгрузки и оптимизации сети в Windows Server 2016 относятся возможности и технологии Software Only (SO), интегрированные возможности и технологии Software and Hardware (SH), а также возможности и технологии Hardware Only (HO).</p>
                        <p>Кроме того, доступна следующая документация по технологиям разгрузки и оптимизации.<p>
                        <hr />
                        <a href="technologies/conv-nic/cnic-top.md">Сетевая карта с согласованным сетевым интерфейсом (NIC)</a>
                        <hr />
                        <a href="technologies/dcb/dcb-top.md">Мост центра обработки данных (DCB)</a>
                        <hr />
                        <a href="technologies/vrss/vrss-top.md">Виртуальное масштабирование на стороне приема (vRSS)</a>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <hr />
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-network.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><a href="technologies/nps/nps-top.md">Сервер политики сети</a></h3>
                        <hr />
                        <p>Сервер сетевых политик (NPS) позволяет создавать и применять политики доступа к сети на уровне организации для проверки подлинности и авторизации сетевых подключений.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <hr />
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-network.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><a href="technologies/netsh/netsh.md">Сетевая оболочка (Netsh)</a></h3>
                        <hr />
                        <p>Сетевую программу сетевой оболочки (Netsh) можно использовать для управления сетевыми технологиями в Windows Server 2016 и Windows 10.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <hr />
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-network.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><a href="technologies/network-subsystem/net-sub-performance-top.md">Настройка производительности сетевой подсистемы</a></h3>
                        <hr />
                        <p>В этом разделе содержатся сведения о выборе правильного сетевого адаптера для рабочей нагрузки сервера, упорядочивания сетевых интерфейсов, связанных с сетью счетчиков производительности, а также сетевых адаптеров настройки производительности и связанных сетевых технологий, таких как Масштабирование на стороне приема (RSS), объединение на стороне приема (RSC) и др.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <hr />
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-network.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><a href="technologies/nic-teaming/NIC-Teaming.md">Поддержка групп сетевых адаптеров</a></h3>
                        <hr />
                        <p>Объединение сетевых карт позволяет сгруппировать физические сетевые адаптеры Ethernet в один или несколько программных виртуальных сетевых адаптеров. Эти виртуальные сетевые адаптеры обеспечивают высокую производительность и отказоустойчивость в случае сбоя сетевого адаптера.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <hr />
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-network.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><a href="technologies/qos/qos-policy-top.md">Политика качества обслуживания (QoS)</a></h3>
                        <hr />
                        <p>Вы можете использовать политику качества обслуживания как централизованное средство управления пропускной способностью сети для всей инфраструктуры Active Directory, создавая профили качества обслуживания, параметры которых распространяются с помощью групповой политики.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <hr />
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-network.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><a href="technologies/wins/wins-top.md">Служба WINS</a></h3>
                        <hr />
                        <p>WINS — это традиционная служба регистрации и разрешения имен компьютеров, которая сопоставляет NetBIOS-имена компьютеров с IP-адресами. Рекомендуется использовать службу DNS вместо WINS.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <hr />
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-network.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><a href="../remote/remote-access/remote-access.md">Удаленный доступ</a></h3>
                        <hr />
                        <p>Вы можете использовать такие технологии удаленного доступа, как DirectAccess и виртуальная частная сеть (VPN), чтобы предоставить удаленным сотрудникам возможность подключения к внутренним сетевым ресурсам. Кроме того, можно использовать удаленный доступ для маршрутизации по локальной сети, а также для прокси-службы веб приложения. Он предоставляет функции обратного прокси-сервера для веб-приложений в корпоративной сети, что делает их доступными для пользователей с любых устройств из-за пределов корпоративной сети.</p>
                        <p>Дополнительные сведения о прокси веб-приложения, который является службой роли сервера удаленного доступа, см. <a href="https://docs.microsoft.com/windows-server/remote/remote-access/web-application-proxy/web-application-proxy-windows-server">в разделе прокси веб-приложения в Windows server 2016</a> .</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <hr />
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-network.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><a href="https://docs.microsoft.com/virtualization/windowscontainers/container-networking/architecture">Сетевые подключения контейнеров Windows</a></h3>
                        <hr />
                        <p>Сетевые подключения контейнеров Windows позволяют создавать и контролировать сети ими для подключения конечных точек контейнеров на узлах Windows 10 и Windows Server с помощью стандартных средств и рабочих процессов. Сетевые подключения контейнеров Windows поддерживают несколько топологий, такие как частные, плоские уровня 2 и маршрутизируемые уровня 3.</p>
                        <p>Кроме того, поддерживаются наложения, которые можно создать локально на узле с помощью DOCKER, Kubernetes или Windows PowerShell через подключаемые модули, взаимодействующие с сетью Windows Host Network Service (HNS). Вы можете создавать сети кластеров с несколькими узлами и управлять ими через системы оркестрации более высокого уровня, используя локальный агент в службе HNS каждого узла.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <hr />
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-network.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><a href="../remote/remote-access/vpn/vpn-top.md">Виртуальная частная сеть (VPN)</a></h3>
                        <hr />
                        <p>DirectAccess и VPN являются службой роли в роли сервера удаленного доступа.</p>
                        <p>При установке удаленного доступа в качестве VPN-сервера можно использовать виртуальную частную сеть (VPN) для предоставления удаленным сотрудникам подключений к сети Организации через Интернет, одновременно сохраняя конфиденциальность информации с помощью зашифрованных подключений. .</p>
                        <p> При использовании VPN удаленного доступа Windows Server (и клиентских компьютеров с Windows 10) вы можете развернуть постоянно подключенный VPN-профиль. Такой вид VPN позволяет управлять удаленными клиентами VPN, которые всегда подключены, а также обеспечивает удобные условия работы для удаленных сотрудников, которым больше не нужно вручную подключаться и отключаться из VPN к сети вашей организации.</p>
                        <p>Дополнительные сведения см. в статье <a href="https://docs.microsoft.com/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/always-on-vpn-deploy">Always on удаленного доступа к развертыванию VPN для Windows Server 2016 и Windows 10</a> .</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
</ul>

## <a name="additional-resources"></a>Дополнительные ресурсы

Сетевые ресурсы для операционных систем более ранних версий, чем Windows Server 2016, доступны в следующих расположениях.

- [Обзор сетевого взаимодействия](https://technet.microsoft.com/library/hh831357.aspx) в Windows Server 2012 и Windows Server 2012 R2
- [Возможности работы с сетями](https://technet.microsoft.com/library/cc753940) в Windows Server 2008 и Windows Server 2008 R2
- [Устаревшее содержимое Windows server 2003 Windows server 2003/2003 R2](https://www.microsoft.com/download/details.aspx?id=53314)
