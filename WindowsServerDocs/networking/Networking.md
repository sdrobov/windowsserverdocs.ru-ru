---
title: Сеть
description: В этом разделе представлен обзор технологий программно-конфигурируемой сети и сетевой платформы, которые доступны в Windows Server 2016.
ms.prod: windows-server-threshold
layout: LandingPage
ms.technology: networking
ms.topic: landing-page
ms.assetid: daaf6b61-5953-4c2d-b6b8-7c885b552646
manager: dougkim
ms.author: pashort
author: shortpatti
ms.localizationpriority: medium
ms.openlocfilehash: bb5a605ef6438bfa6a2afe4963b8206f9dc84a3a
ms.sourcegitcommit: 07ac08dea2b8f2763c2614a999dc7967018aa0b4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2018
ms.locfileid: "6121403"
---
# Сеть

>[!TIP]
> Ищете дополнительные сведения о старых версиях Windows Server? Ознакомьтесь с другими нашими [библиотеками Windows Server](/previous-versions/windows/) на сайте docs.microsoft.com. Кроме того, вы можете найти нужную информацию [на этом сайте](https://docs.microsoft.com/search/index?search=Windows+Server&dataSource=previousVersions).

<HR />

Сетевое взаимодействие— это основополагающая часть платформы программно-определяемого центра обработки данных (SDDC), и Windows Server2016 предоставляет новые и улучшенные технологии программно-конфигурируемой сети (SDN), помогающие вашей организации перейти на полнофункциональное решение SDDC.

При управлении сетями как программно-определяемым ресурсом можно однократно описать требования к инфраструктуре приложений и затем выбрать место выполнения приложения— локально или в облаке. 

Такая согласованность упрощает масштабирование приложений и позволяет легко запускать их в любом месте с полной уверенностью в безопасности, производительности, качестве обслуживания и доступности.

<HR />

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
                                        <h2><a href="../networking/What-s-New-in-Networking.md">Новые возможности работы с сетями</a></h2>
                                        </div>
                                    </div>
                                </div>
                             </div>
                          </a>
                        </li>
                     </ul>
<HR />

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
                                        <h3><a href="https://docs.microsoft.com/windows-server/networking/sdn/">Программно-конфигурируемая сеть (SDN)</a><hr /></h3>Этот раздел поможет получить представление о технологиях программно-конфигурируемых сетей, входящих в состав Windows Server System Center и Microsoft Azure.</p>
                        
                                        <p><b>Примечание.</b> Для узлов и виртуальных машин (ВМ) Hyper-V, на которых выполняются серверы инфраструктуры SDN, такие как узлы сетевого контроллера и программной балансировки нагрузки, необходимо установить выпуск Windows Server Datacenter. Для узлов Hyper-V, содержащих только ВМ рабочих нагрузок клиентов, которые подключены к сетям, управляемым SDN, можно использовать выпуск Windows Server Standard.</p>                                        </div>
                                    </div>
                                </div>
                            </div>
                          </a>
                        </li>
<HR />
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
                                        <h3><a href="sdn/deploy/Deploy-a-Software-Defined-Network-infrastructure-using-scripts.md">Развертывание инфраструктуры программно-конфигурируемой сети с помощью скриптов</a><hr /></h3>Это руководство содержит инструкции по развертыванию сетевого контроллера с виртуальными сетями и шлюзами в тестовой лабораторной среде.</p>                                        </div>
                                    </div>
                                </div>
                            </div>
                          </a>
                        </li>
<HR />
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
                                        <h3><a href="sdn/technologies/network-controller/Network-Controller.md">Сетевой контроллер</a><hr /></h3>Сетевой контроллер обеспечивает централизованную программируемую точку автоматизации для управления, настройки, мониторинга, а также выявления и устранения неисправностей в виртуальной и физической сетевой инфраструктуре центра данных.</p>                                        </div>
                                    </div>
                                </div>
                            </div>
                          </a>
                        </li>
<HR />
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
                                        <h3><a href="sdn/technologies/network-function-virtualization/software-load-balancing-for-sdn.md">Программная балансировка нагрузки (SLB) для SDN</a><hr /></h3>Поставщики облачных служб (CSP) и предприятия, развертывающие программно-конфигурируемые сети (SDN) в Windows Server2016, могут использовать программную балансировку нагрузки (SLB), чтобы равномерно распределить сетевой трафик клиента и его заказчика между ресурсами виртуальной сети. Windows Server SLB позволяет размещать одну и ту же рабочую нагрузку на нескольких серверах, что обеспечивает высокий уровень доступности и масштабирование.</p>                                        </div>
                                    </div>
                                </div>
                            </div>
                          </a>
                        </li>
<HR />
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
                                        <h3><a href="sdn/technologies/network-function-virtualization/RAS-Gateway-for-SDN.md">Шлюз RAS-сервера для SDN</a><hr /></h3>Шлюз RAS, который представляет собой находится программный мультитенантный маршрутизатор с поддержкой протокола BGP в Windows Server2016, предназначен для поставщиков облачных служб (CSP) и предприятий, которые размещают несколько виртуальных сетей клиента с помощью виртуализации сети Hyper-V.</p>                                        </div>
                                    </div>
                                </div>
                            </div>
                          </a>
                        </li>
<HR />
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
                                        <h3><a href="sdn/technologies/network-function-virtualization/Network-Function-Virtualization.md">Виртуализация сетевых функций</a><hr /></h3>В программно-определяемых центрах обработки данных сетевые функции, выполняемые аппаратными устройствами (такими как подсистемы балансировки нагрузки, брандмауэры, маршрутизаторы, коммутаторы и т.д), все чаще виртуализируются в виде виртуальных устройств. Такая "виртуализация сетевых функций" является естественным этапом развития виртуализации серверов и сетей.</p>                                        </div>
                                    </div>
                                </div>
                            </div>
                          </a>
                        </li>
<HR />
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
                                        <h3><a href="sdn/technologies/network-function-virtualization/Datacenter-Firewall-Overview.md">Обзор брандмауэра центра обработки данных</a><hr /></h3>Брандмауэр центра обработки данных—брандмауэр сетевого уровня с пятью кортежами (протокол, номера начального и конечного портов, начальный и конечный IP-адреса), с функцией отслеживания состояния и поддержкой нескольких клиентов.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
</ul>

<HR />

## <a name="bkmk_networking"></a>Технологии сетевого взаимодействия

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
                                        <h3><a href="branchcache/BranchCache.md">BranchCache</a><hr /></h3>
                                        <p>BranchCache— это технология оптимизации пропускной способности глобальной сети (WAN). Для оптимизации пропускной способности глобальной сети служба BranchCache получает данные с серверов содержимого в главном офисе или облаке и помещает их в кэш на компьютерах филиала, когда пользователи получают доступ к содержимому на удаленных серверах, что позволяет обеспечить для клиентских компьютеров в филиалах локальный доступ к данным вместо доступа по глобальной сети.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
<HR />
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
                                        <h3><a href="core-network-guide/core-network-guide-windows-server.md">Руководство по основной сети</a><hr /></h3>
                                        <p>Узнайте, как развернуть сеть Windows Server с помощью руководства по основной сети, а также добавить компоненты в сетевое развертывание с помощью вспомогательных руководств по основной сети.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
<HR />
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
                                        <h3><a href="../remote/remote-access/directaccess/DirectAccess.md">DirectAccess</a><hr /></h3>
                                        <p>DirectAccess предоставляет удаленным пользователям возможность подключения к сетевым ресурсам организации. </p>
                    </div>
                </div>
            </div>
        </div>
    </li>
<HR />
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
                                        <h3><a href="dns/dns-top.md">Служба доменных имен (DNS)</a><hr /></h3>
                                        <p>Служба доменных имен DNS представляет собой один из стандартных в отрасли наборов протоколов, реализующих взаимодействие TCP/IP, а DNS-клиент и DNS-сервер совместно предоставляют службы разрешения имен при сопоставлении имен с IP-адресами для компьютеров и пользователей.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
<HR />
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
                                        <h3><a href="technologies/dhcp/dhcp-top.md">Протокол DHCP</a><hr /></h3>
                                        <p>DHCP— это протокол клиент-сервер, который автоматически предоставляет IP-узлу его IP-адрес и другие связанные сведения о конфигурации, такие как маска подсети и шлюз по умолчанию.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
<HR />
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
                                        <h3><a href="sdn/technologies/hyper-v-network-virtualization/Hyper-V-Network-Virtualization.md">Виртуализация сети Hyper-V</a><hr /></h3>
                                        <p>Виртуализация сети Hyper-V HNV обеспечивает виртуализацию сетей клиентов на основе общей физической сетевой инфраструктуры.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
<HR />
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
                                        <h3><a href="../virtualization/hyper-v-virtual-switch/Hyper-V-Virtual-Switch.md">Виртуальный коммутатор Hyper-V</a><hr /></h3>
                                        <p>Виртуальный коммутатор Hyper-V — это программный сетевой коммутатор Ethernet уровня 2, который доступен в диспетчере Hyper-V при установке роли сервера Hyper-V. Коммутатор предоставляет программно управляемые и расширяемые возможности для подключения виртуальных машин к виртуальным сетям и к физической сети. Виртуальный коммутатор Hyper-V также обеспечивает применение политик в области безопасности, изоляции и уровней обслуживания. </p>
                    </div>
                </div>
            </div>
        </div>
    </li>
<HR />
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
                                        <h3><a href="technologies/ipam/ipam-top.md">Управление IP-адресами (IPAM)</a><hr /></h3>
                                        <p>Управление IP-адресами IPAM— это встроенный набор инструментов для сквозного планирования, развертывания, администрирования и отслеживания инфраструктуры IP-адресов в многофункциональном пользовательском интерфейсе. IPAM автоматически определяет серверы инфраструктуры IP-адресов и DNS-серверы в вашей сети и позволяет управлять ими из центрального интерфейса. </p>
                    </div>
                </div>
            </div>
        </div>
    </li>
<HR />
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
                                        <h3><a href="technologies/Network-Load-Balancing.md">Балансировка сетевой нагрузки</a><hr /></h3>
                                        <p>Балансировка сетевой нагрузки NLB распределяет трафик между несколькими серверами, используя сетевой протокол TCP/IP. Для развертываний, отличных от SDN, NLB обеспечивает масштабируемость приложений без учета состояния, таких как веб-серверы с запущенными службами IIS, за счет добавления дополнительных серверов по мере увеличения нагрузки.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
<HR />
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
                                        <h3><a href="technologies/hpn/hpn-top.md">Высокопроизводительные сети</a><hr /></h3>
                                        <p>К технологиям разгрузки и оптимизации сети в Windows Server 2016 относятся возможности и технологии Software Only (SO), интегрированные возможности и технологии Software and Hardware (SH), а также возможности и технологии Hardware Only (HO).</p>

                                        <p>Кроме того, доступна следующая документация по технологиям разгрузки и оптимизации.<p>
                                        <hr />
                                        <a href="technologies/conv-nic/cnic-top.md">Высокопроизводительные сети</a><hr />
                                        <a href="technologies/dcb/dcb-top.md">Мост для центра обработки данных</a><hr />
                                        <a href="technologies/vrss/vrss-top.md">Виртуальное масштабирование на стороне приема (vRSS)</a>
                    </div>
                </div>
            </div>
        </div>
    </li>
<HR />
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
                                        <h3><a href="technologies/nps/nps-top.md">Сервер политики сети</a><hr /></h3>
                                        <p>
Сервер сетевых политик (NPS) позволяет создавать и применять политики доступа к сети на уровне организации для проверки подлинности и авторизации сетевых подключений.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
<HR />
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
                                        <h3><a href="technologies/netsh/netsh.md">Сетевая оболочка (Netsh)</a><hr /></h3>
                                        <p>
Вы можете использовать служебную программу сетевой оболочки (netsh) для управления сетевыми технологиями в Windows Server 2016 и Windows 10.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
<HR />
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
                                        <h3><a href="technologies/network-subsystem/net-sub-performance-top.md">Настройка производительности сетевой подсистемы</a><hr /></h3>
                                        <p>
В этом разделе представлена информация о выборе правильного сетевого адаптера для рабочей нагрузки вашего сервера, упорядочивании сетевых интерфейсов, счетчиков производительности сети, сетевых адаптеров с настройкой производительности и других сетевых технологий, таких как масштабирование на стороне приема (RSS), объединение на стороне приема (RSC) и другие.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
<HR />
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
                                        <h3><a href="technologies/nic-teaming/NIC-Teaming.md">Объединение сетевых карт</a><hr /></h3>
                                        <p>
Объединение сетевых карт позволяет сгруппировать физические сетевые адаптеры Ethernet в один или несколько программных виртуальных сетевых адаптеров. Эти виртуальные сетевые адаптеры обеспечивают высокую производительность и отказоустойчивость в случае сбоя сетевого адаптера.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
<HR />
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
                                        <h3><a href="technologies/qos/qos-policy-top.md">Политика качества обслуживания (QoS)</a><hr /></h3>
                                        <p>
Вы можете использовать политику качества обслуживания как централизованное средство управления пропускной способностью сети для всей инфраструктуры Active Directory, создавая профили качества обслуживания, параметры которых распространяются с помощью групповой политики.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
<HR />
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
                                        <h3><a href="technologies/wins/wins-top.md">Служба WINS</a><hr /></h3>
                                        <p>
WINS— это традиционная служба регистрации и разрешения имен компьютеров, которая сопоставляет NetBIOS-имена компьютеров с IP-адресами. Рекомендуется использовать службу DNS вместо WINS.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
<HR />
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
                                        <h3><a href="../remote/remote-access/remote-access.md">Удаленный доступ</a><hr /></h3>
                                        <p>
Вы можете использовать технологии удаленного доступа, такие как DirectAccess и виртуальные частные сети (VPN), для предоставления удаленным сотрудникам возможности подключения к внутренним сетевым ресурсам. Кроме того, вы можете использовать удаленный доступ для маршрутизации локальной сети и для реализации прокси-сервера веб-приложений. Он предоставляет функции обратного прокси-сервера для веб-приложений в корпоративной сети, что делает их доступными для пользователей с любых устройств из-за пределов корпоративной сети.</p>

                                        <p>Дополнительные сведения о прокси-сервере веб-приложения, который является службой роли сервера удаленного доступа, см. в разделе <a href="https://docs.microsoft.com/windows-server/remote/remote-access/web-application-proxy/web-application-proxy-windows-server">Прокси-сервер веб-приложений в Windows Server 2016.</a></p>
                    </div>
                </div>
            </div>
        </div>
    </li>
<HR />
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
                                        <h3><a href="https://docs.microsoft.com/virtualization/windowscontainers/container-networking/architecture">Сетевые подключения контейнеров Windows</a><hr /></h3>
                                        <p>
Сетевые подключения контейнеров Windows позволяют создавать и контролировать сети ими для подключения конечных точек контейнеров на узлах Windows 10 и Windows Server с помощью стандартных средств и рабочих процессов. Сетевые подключения контейнеров Windows поддерживают несколько топологий, такие как частные, плоские уровня 2 и маршрутизируемые уровня 3.</p>

                                        <p>Кроме того, поддерживаются сети наложения, которые можно создавать локально на узле с помощью Docker, Kubernetes или Windows PowerShell, используя подключаемые модули, которые обмениваться данными со службой сети узла Windows (HNS). Вы можете создавать и контролировать кластерные сети с несколькими узлами с помощью высокоуровневых систем оркестрации, взаимодействуя со службой HNS каждого узла через локальный агент.</p>
                    </div>
                </div>
            </div>
        </div>
    </li>
<HR />
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
                                        <h3><a href="../remote/remote-access/vpn/vpn-top.md">Виртуальная частная сеть (VPN)</a><hr /></h3>
                                        <p>
DirectAccess и VPN являются службой роли в роли сервера удаленного доступа.</p>

                                        <p>При установке удаленного доступа в качестве VPN-сервера можно использовать виртуальную частную сеть (VPN) для предоставления удаленным сотрудникам подключения к сети организации через Интернет, одновременно обеспечивая конфиденциальность данных с помощью шифрования подключений.</p>

                                       <p> При использовании VPN удаленного доступа Windows Server (и клиентских компьютеров с Windows 10) вы можете развернуть постоянно подключенный VPN-профиль. Такой вид VPN позволяет управлять удаленными клиентами VPN, которые всегда подключены, а также обеспечивает удобные условия работы для удаленных сотрудников, которым больше не нужно вручную подключаться и отключаться из VPN к сети вашей организации.</p>

                                       <p>Дополнительные сведения см. в разделе <a href="https://docs.microsoft.com/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/always-on-vpn-deploy">Руководство по развертыванию постоянно подключенной сети VPN удаленного доступа для Windows Server 2016 и Windows 10.</a></p>
                    </div>
                </div>
            </div>
        </div>
    </li>
</ul>

## Дополнительные ресурсы

Сетевые ресурсы для операционных систем более ранних версий, чем Windows Server2016, доступны в следующих расположениях.

- [Обзор сетевого взаимодействия](https://technet.microsoft.com/library/hh831357.aspx) в Windows Server2012 и Windows Server2012 R2
- [Возможности работы с сетями](https://technet.microsoft.com/library/cc753940) в Windows Server2008 и Windows Server2008R2
- Windows Server 2003 [Устаревший контент Windows Server 2003/2003 R2](https://www.microsoft.com/download/details.aspx?id=53314)
