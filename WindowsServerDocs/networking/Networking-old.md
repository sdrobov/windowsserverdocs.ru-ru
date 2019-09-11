---
title: Сети
description: В этом разделе представлен обзор технологий программно-конфигурируемой сети и сетевой платформы, которые доступны в Windows Server 2016.
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.date: 05/08/2018
ms.assetid: daaf6b61-5953-4c2d-b6b8-7c885b552646
manager: dougkim
ms.author: pashort
author: shortpatti
ms.localizationpriority: medium
ms.openlocfilehash: cf0aa1d752167962c11171ad98ae26591a740221
ms.sourcegitcommit: f6490192d686f0a1e0c2ebe471f98e30105c0844
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70868988"
---
# <a name="networking"></a>Сети

>Относится к: Windows Server (Semi-Annual Channel), Windows Server 2016

>[!TIP]
> Ищете дополнительные сведения о старых версиях Windows Server? Ознакомьтесь с другими нашими [библиотеками Windows Server](/previous-versions/windows/) на сайте docs.microsoft.com. Кроме того, вы можете найти нужную информацию [на этом сайте](https://docs.microsoft.com/search/index?search=Windows+Server&dataSource=previousVersions).

<img src="../media/landing-icons/network.png" style='float:left; padding:.5em;' alt="Icon depicting two networked computers"> Сеть — это \(базовая часть платформы SDDC\) , определяемая программным обеспечением центра обработки данных, и Windows Server 2016 предоставляет новые и улучшенные\) программно определяемые сетевые \(технологии Sdn, которые помогут вам перейти к полностью реализованное решение SDDC для вашей организации.

При управлении сетями в качестве программно определенного ресурса можно описать требования к инфраструктуре приложения один раз, а затем выбрать, где приложение выполняется локально или в облаке. 

Такая согласованность упрощает масштабирование приложений и позволяет легко запускать их в любом месте с полной уверенностью в безопасности, производительности, качестве обслуживания и доступности.

>[!Note]
> Чтобы скачать Windows Server, см. статью [Ознакомительные версии Windows Server](https://www.microsoft.com/evalcenter/evaluate-windows-server-technical-preview).

Windows Server 2016 добавляет следующие новые технологии сетевого взаимодействия:

- Программно определяемая сеть: Сетевой контроллер обеспечивает централизованную программируемую точку автоматизации для управления, настройки, мониторинга, а также выявления и устранения неисправностей в виртуальной и физической сетевой инфраструктуре центра данных. Сетевой контроллер позволяет использовать виртуализацию сетевых функций, чтобы легко развертывать виртуальные \(машины\) виртуальных машин\) для балансировки \(нагрузки программного обеспечения, чтобы оптимизировать загрузку сетевого трафика для клиентов и RAS. Шлюзы для предоставления клиентам необходимых вариантов подключения между Интернетом, локальными и облачными ресурсами. Сетевой контроллер также можно использовать для управления брандмауэром центра обработки данных на виртуальных машинах и узлах Hyper-V.

- Сетевая платформа: С помощью новых возможностей существующих технологий сетевой платформы можно использовать политику DNS для настройки ответов DNS-сервера на запросы, использовать объединенный сетевой адаптер, обрабатывающий комбинированный \(RDMA\) и трафик Ethernet. для создания виртуальных коммутаторов Hyper \(-V, подключенных к сетевым картам RDMA, используйте команду коммутатора коммутации внедренных\) команд \(, а для управления зонами и серверами DNS, а также DHCP и IP-адресами используется IPAM управления IP-адресами.\)

Дополнительные сведения см. в разделе [Поддерживаемые сценарии сетевого взаимодействия в Windows Server](windows-server-supported-networking-scenarios.md).

В следующих разделах представлены сведения о технологиях SDN и сетевой платформы.

## <a name="software-defined-networking-technologies"></a>Технологии программно-конфигурируемых сетей

### <a name="software-defined-networking-40sdn41sdnsoftware-defined-networkingmd"></a>[Программно определяемая сетевая &#40;Sdn&#41;](sdn/software-defined-networking.md)

Этот раздел поможет получить представление о технологиях программно-конфигурируемых сетей, входящих в состав Windows Server System Center и Microsoft Azure.

>[!NOTE]
>Для узлов и виртуальных машин \(\) Hyper-V, на которых выполняются серверы инфраструктуры Sdn, такие как узлы сетевого контроллера и программной балансировки нагрузки, необходимо установить Windows Server 2016 Datacenter Edition. Для узлов Hyper-V, содержащих только виртуальные машины рабочей нагрузки клиента, подключенные\-к управляемым Sdn, можно использовать Windows Server 2016 Standard Edition.

### <a name="deploy-a-software-defined-network-infrastructure-using-scriptssdndeploydeploy-a-software-defined-network-infrastructure-using-scriptsmd"></a>[Развертывание программно-определяемой сетевой инфраструктуры с помощью сценариев](sdn/deploy/Deploy-a-Software-Defined-Network-infrastructure-using-scripts.md)
Это руководство содержит инструкции по развертыванию сетевого контроллера с виртуальными сетями и шлюзами в тестовой лабораторной среде.

### <a name="network-controllersdntechnologiesnetwork-controllernetwork-controllermd"></a>[Сетевой контроллер](sdn/technologies/network-controller/Network-Controller.md)

Сетевой контроллер обеспечивает централизованную программируемую точку автоматизации для управления, настройки, мониторинга, а также выявления и устранения неисправностей в виртуальной и физической сетевой инфраструктуре центра данных.

### <a name="software-load-balancing-40slb41-for-sdnsdntechnologiesnetwork-function-virtualizationsoftware-load-balancing-for-sdnmd"></a>[Подсистема &#40;балансировки&#41; нагрузки ПРОГРАММного обеспечения для Sdn](sdn/technologies/network-function-virtualization/software-load-balancing-for-sdn.md)

Поставщики \(облачных служб\) CSP и предприятия, которые развертывают программно-определяемую сеть (SDN) в Windows Server 2016 \(\) , могут использовать подсистему балансировки нагрузки программного обеспечения для равномерного распределения клиента и клиента. сетевой трафик клиента между ресурсами виртуальной сети. Windows Server SLB позволяет размещать одну и ту же рабочую нагрузку на нескольких серверах, что обеспечивает высокий уровень доступности и масштабирование.

### <a name="ras-gateway-for-sdnsdntechnologiesnetwork-function-virtualizationras-gateway-for-sdnmd"></a>[Шлюз RAS-сервера для SDN](sdn/technologies/network-function-virtualization/RAS-Gateway-for-SDN.md)

Шлюз RAS, который представляет собой программный, многоклиентский, протокол BGP \(маршрутизатор\) с поддержкой BGP в Windows Server 2016, предназначен\) для поставщиков \(облачных служб и организаций, на которых размещается несколько виртуальных сетей клиентов, использующих виртуализацию сети Hyper-V. 

### <a name="network-function-virtualizationsdntechnologiesnetwork-function-virtualizationnetwork-function-virtualizationmd"></a>[Виртуализация сетевой функции](sdn/technologies/network-function-virtualization/Network-Function-Virtualization.md)

В программно определенных центрах обработки данных сетевые функции, выполняемые аппаратными устройствами \(, такими как подсистемы балансировки нагрузки, брандмауэры, маршрутизаторы, коммутаторы\) и т. д., все чаще виртуализованы как виртуальные устройства. Такая "виртуализация сетевых функций" является естественным этапом развития виртуализации серверов и сетей.

### <a name="datacenter-firewall-overviewsdntechnologiesnetwork-function-virtualizationdatacenter-firewall-overviewmd"></a>[Обзор брандмауэра центра обработки данных](sdn/technologies/network-function-virtualization/Datacenter-Firewall-Overview.md)

Брандмауэр центра обработки данных —брандмауэр сетевого уровня с пятью кортежами (протокол, номера начального и конечного портов, начальный и конечный IP-адреса), с функцией отслеживания состояния и поддержкой нескольких клиентов.

## <a name="bkmk_networking"></a>Сетевые технологии

Приведенная ниже таблица содержит ссылки на некоторые технологии сетевого взаимодействия в Windows Server 2016.

### <a name="whats-new-in-networkingnetworkingwhat-s-new-in-networkingmd"></a>[Новые возможности работы в сети](../networking/What-s-New-in-Networking.md)

Прочитайте следующие разделы, чтобы ознакомиться с новыми сетевыми технологиями и новыми функциями для существующих технологий в Windows Server 2016.

### <a name="branchcachebranchcachebranchcachemd"></a>[BranchCache](branchcache/BranchCache.md)

BranchCache — это расширенная технология \(оптимизации\) пропускной способности глобальной сети. Для оптимизации пропускной способности глобальной сети служба BranchCache получает данные с серверов содержимого в главном офисе или облаке и помещает их в кэш на компьютерах филиала, когда пользователи получают доступ к содержимому на удаленных серверах, что позволяет обеспечить для клиентских компьютеров в филиалах локальный доступ к данным вместо доступа по глобальной сети.

### <a name="core-network-guide-for-windows-server-2016core-network-guidecore-network-guide-windows-servermd"></a>[Основное сетевое руководством для Windows Server 2016](core-network-guide/core-network-guide-windows-server.md)

Узнайте, как развернуть сеть Windows Server с помощью руководства по основной сети, а также добавить компоненты в сетевое развертывание с помощью вспомогательных руководств по основной сети.

### <a name="directaccessremoteremote-accessdirectaccessdirectaccessmd"></a>[DirectAccess](../remote/remote-access/directaccess/DirectAccess.md)

DirectAccess предоставляет удаленным пользователям возможность подключения к сетевым ресурсам организации. 

Документация DirectAccess теперь находится в разделе [Удаленный доступ и управление серверами](https://docs.microsoft.com/windows-server/remote/) оглавления Windows Server 2016 в разделе [Удаленный доступ](https://docs.microsoft.com/windows-server/remote/remote-access/remote-access). Дополнительные сведения см. в разделе [DirectAccess](../remote/remote-access/directaccess/DirectAccess.md).

### <a name="domain-name-system-40dns41dnsdns-topmd"></a>[DNS-сервер &#40;системы доменных имен&#41;](dns/dns-top.md)

Служба доменных имен \(DNS\) представляет собой один из стандартных в отрасли наборов протоколов, реализующих взаимодействие TCP/IP, а DNS-клиент и DNS-сервер совместно предоставляют службы разрешения имен при сопоставлении имен с IP-адресами для компьютеров и пользователей.

### <a name="dynamic-host-configuration-protocol-40dhcp41technologiesdhcpdhcp-topmd"></a>[DHCP протокол &#40;динамической настройки узла&#41;](technologies/dhcp/dhcp-top.md)

Протокол \(динамической настройки узла DHCP\) — это протокол клиента или сервера, который автоматически предоставляет IP- \(\) адрес протокола Интернета и другие связанные сведения о конфигурации, такие как в качестве маски подсети и шлюза по умолчанию.

### <a name="hyper-v-network-virtualizationsdntechnologieshyper-v-network-virtualizationhyper-v-network-virtualizationmd"></a>[Виртуализация сети Hyper-V](sdn/technologies/hyper-v-network-virtualization/Hyper-V-Network-Virtualization.md)

Виртуализация сети Hyper-V \(HNV\) обеспечивает виртуализацию сетей клиентов на основе общей физической сетевой инфраструктуры.

### <a name="hyper-v-virtual-switchvirtualizationhyper-v-virtual-switchhyper-v-virtual-switchmd"></a>[Виртуальный коммутатор Hyper-V](../virtualization/hyper-v-virtual-switch/Hyper-V-Virtual-Switch.md)

Виртуальный коммутатор Hyper-V — это программный сетевой коммутатор Ethernet уровня 2, который доступен в диспетчере Hyper-V при установке роли сервера Hyper-V. Коммутатор предоставляет программно управляемые и расширяемые возможности для подключения виртуальных машин к виртуальным сетям и к физической сети. Виртуальный коммутатор Hyper-V также обеспечивает применение политик в области безопасности, изоляции и уровней обслуживания. 

Документация по виртуальному коммутатору Hyper-V теперь находится в разделе **Виртуализация** оглавления Windows Server 2016. Дополнительные сведения см. в разделе [Виртуальный коммутатор Hyper-V](../virtualization/hyper-v-virtual-switch/Hyper-V-Virtual-Switch.md).

### <a name="ip-address-management-40ipam41technologiesipamipam-topmd"></a>[IPAM по управлению &#40;IP-адресами&#41;](technologies/ipam/ipam-top.md)

Управление IP-адресами \(IPAM\) — это встроенный набор инструментов для сквозного планирования, развертывания, администрирования и отслеживания инфраструктуры IP-адресов в многофункциональном пользовательском интерфейсе. IPAM автоматически обнаруживает серверы инфраструктуры IP-адресов и DNS- \(\) серверы системы доменных имен в сети и позволяет управлять ими из центрального интерфейса.

### <a name="network-load-balancingtechnologiesnetwork-load-balancingmd"></a>[Балансировка сетевой нагрузки](technologies/Network-Load-Balancing.md)

Балансировка сетевой нагрузки \(NLB\) распределяет трафик между несколькими серверами, используя сетевой протокол TCP/IP. Для развертываний, отличных от Sdn, балансировка сетевой нагрузки гарантирует, что приложения без отслеживания \(состояния\), такие как веб-серверы, работающие службы IIS IIS, будут масштабироваться путем добавления дополнительных серверов при увеличении нагрузки.

### <a name="high-performance-networkingtechnologieshpnhpn-topmd"></a>[Высокопроизводительные сети](technologies/hpn/hpn-top.md)

К технологиям разгрузки и оптимизации сети в Windows Server 2016 относятся возможности и технологии Software Only (SO), интегрированные возможности и технологии Software and Hardware (SH), а также возможности и технологии Hardware Only (HO).

Кроме того, доступна следующая документация по технологиям разгрузки и оптимизации.

- [Путеводитель по настройке сетевого адаптера с согласованным интерфейсом](technologies/conv-nic/cnic-top.md)
- [Мост центра обработки данных (DCB)](technologies/dcb/dcb-top.md)
- [Виртуальное масштабирование на стороне приема (vRSS)](technologies/vrss/vrss-top.md)


### <a name="network-policy-servertechnologiesnpsnps-topmd"></a>[Сервер политики сети](technologies/nps/nps-top.md)

Сервер сетевых политик (NPS) позволяет создавать и применять политики доступа к сети на уровне организации для проверки подлинности и авторизации сетевых подключений.

### <a name="network-shell-netshtechnologiesnetshnetshmd"></a>[Сетевая оболочка (Netsh)](technologies/netsh/netsh.md)

Служебную программу Netsh\) Network Shell \(можно использовать для управления сетевыми технологиями в Windows Server 2016 и Windows 10.

### <a name="network-subsystem-performance-tuningtechnologiesnetwork-subsystemnet-sub-performance-topmd"></a>[Настройка производительности сетевой подсистемы](technologies/network-subsystem/net-sub-performance-top.md)

В этом разделе содержатся сведения о выборе правильного сетевого адаптера для рабочей нагрузки сервера, упорядочивания сетевых интерфейсов, связанных с сетью счетчиков производительности, а также сетевых адаптеров настройки производительности и связанных сетевых технологий, таких как Получение RSS- \(канала\)для масштабирования на стороне \(приема\), объединение RSC и др.

### <a name="nic-teamingtechnologiesnic-teamingnic-teamingmd"></a>[Поддержка групп сетевых адаптеров](technologies/nic-teaming/NIC-Teaming.md)

Объединение сетевых карт позволяет сгруппировать физические сетевые адаптеры Ethernet в один или несколько программных виртуальных сетевых адаптеров. Эти виртуальные сетевые адаптеры обеспечивают высокую производительность и отказоустойчивость в случае сбоя сетевого адаптера.

### <a name="quality-of-service-qos-policytechnologiesqosqos-policy-topmd"></a>[Политика качества обслуживания (QoS)](technologies/qos/qos-policy-top.md)

Вы можете использовать политику качества обслуживания как централизованное средство управления пропускной способностью сети для всей инфраструктуры Active Directory, создавая профили качества обслуживания, параметры которых распространяются с помощью групповой политики.

### <a name="remote-accessremoteremote-accessremote-accessmd"></a>[Удаленный доступ](../remote/remote-access/remote-access.md)

Для предоставления удаленным сотрудникам возможности подключения к внутренним сетевым ресурсам можно использовать \(такие\) технологии удаленного доступа, как DirectAccess и виртуальная частная сеть VPN. Кроме того, можно использовать удаленный доступ для локальной сетевой \(\) маршрутизации, а также для прокси-службы веб приложения. Он предоставляет функции обратного прокси-сервера для веб-приложений в корпоративной сети, что делает их доступными для пользователей с любых устройств из-за пределов корпоративной сети.

Документация по удаленному доступа теперь находится в разделе [Удаленный доступ и управление серверами](https://docs.microsoft.com/windows-server/remote/) оглавления Windows Server 2016. Дополнительные сведения см. в разделе [Удаленный доступ](../remote/remote-access/remote-access.md).

Дополнительные сведения о прокси-сервере веб-приложения, который является службой роли сервера удаленного доступа, см. в разделе [Прокси-сервер веб-приложений в Windows Server 2016](https://docs.microsoft.com/windows-server/remote/remote-access/web-application-proxy/web-application-proxy-windows-server).

### <a name="virtual-private-networking-vpnremoteremote-accessvpnvpn-topmd"></a>[Виртуальная частная сеть (VPN)](../remote/remote-access/vpn/vpn-top.md)

В Windows Server 2016 **DirectAccess и VPN** являются службой роли в **роли сервера удаленного доступа**.

При установке удаленного доступа в качестве VPN-сервера можно использовать виртуальную частную \(сеть VPN\) , чтобы предоставить удаленным сотрудникам подключения к сети Организации через Интернет, одновременно сохраняя сведения. конфиденциальность с помощью зашифрованных соединений.

При использовании VPN удаленного доступа Windows Server 2016 (и клиентских компьютеров с Windows 10) вы можете развернуть постоянно подключенный VPN-профиль. Такой вид VPN позволяет управлять удаленными клиентами VPN, которые всегда подключены, а также обеспечивает удобные условия работы для удаленных сотрудников, которым больше не нужно вручную подключаться и отключаться из VPN к сети вашей организации.

Дополнительные сведения см. в разделе [Руководство по развертыванию постоянно подключенной сети VPN удаленного доступа для Windows Server 2016 и Windows 10](https://docs.microsoft.com/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/always-on-vpn-deploy).

>[!NOTE]
>Документация по VPN теперь находится в разделе [Удаленный доступ и управление серверами](https://docs.microsoft.com/windows-server/remote/) оглавления Windows Server 2016 в разделе [Удаленный доступ](https://docs.microsoft.com/windows-server/remote/remote-access/remote-access).

Дополнительные сведения о VPN см. в разделе [Виртуальная частная сеть (VPN)](https://docs.microsoft.com/windows-server/remote/remote-access/vpn/vpn-top).

### <a name="windows-container-networkinghttpsdocsmicrosoftcomvirtualizationwindowscontainersmanage-containerscontainer-networking"></a>[Сетевые подключения контейнеров Windows](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/container-networking)

Сетевые подключения контейнеров Windows позволяют создавать и контролировать сети ими для подключения конечных точек контейнеров на узлах Windows 10 и Windows Server с помощью стандартных средств и рабочих процессов. Сетевые подключения контейнеров Windows поддерживают несколько топологий, такие как частные, плоские уровня 2 и маршрутизируемые уровня 3.

Кроме того, поддерживаются наложения, которые можно создать локально на узле с помощью DOCKER, Kubernetes или Windows PowerShell через подключаемые модули, взаимодействующие со службой \(\)управления сетью узла Windows. Вы можете создавать сети кластеров\-с несколькими узлами и управлять ими через системы оркестрации более высокого уровня, используя локальный агент в службе HNS каждого узла.

### <a name="windows-internet-name-service-winstechnologieswinswins-topmd"></a>[Служба WINS](technologies/wins/wins-top.md)

WINS — это традиционная служба регистрации и разрешения имен компьютеров, которая сопоставляет NetBIOS-имена компьютеров с IP-адресами. Рекомендуется использовать службу DNS вместо WINS.

## <a name="additional-resources"></a>Дополнительные ресурсы

Сетевые ресурсы для операционных систем более ранних версий, чем Windows Server 2016, доступны в следующих расположениях.

- [Обзор сетевого взаимодействия](https://technet.microsoft.com/library/hh831357.aspx) в Windows Server 2012 и Windows Server 2012 R2
- [Возможности работы с сетями](https://technet.microsoft.com/library/cc753940) в Windows Server 2008 и Windows Server 2008 R2
- [Устаревшее содержимое Windows server 2003 Windows server 2003/2003 R2](https://www.microsoft.com/download/details.aspx?id=53314)
