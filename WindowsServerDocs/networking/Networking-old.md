---
title: Сеть
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
ms.openlocfilehash: 7caa99f1b6b9e25e5a6f2c4333b033fb3088195d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59862595"
---
# <a name="networking"></a>Сеть

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

>[!TIP]
> Ищете дополнительные сведения о старых версиях Windows Server? Ознакомьтесь с нашими другими [библиотеками Windows Server](/previous-versions/windows/) на docs.microsoft.com. Кроме того, вы можете найти нужную информацию [на этом сайте](https://docs.microsoft.com/search/index?search=Windows+Server&dataSource=previousVersions).

<img src="../media/landing-icons/network.png" style='float:left; padding:.5em;' alt="Icon depicting two networked computers"> Сеть — это Основополагающая часть программного обеспечения определяемого центра обработки данных \(SDDC\) платформы и Windows Server 2016 предоставляет новые и улучшенные программно-Конфигурируемую сеть \(SDN\) технологии, чтобы помочь вам выполнить переход полнофункциональное решение SDDC для вашей организации.

При управлении сетями как программно-определяемым ресурсом можно однократно описать требования к инфраструктуре приложений и затем выбрать место выполнения приложения — локально или в облаке. 

Такая согласованность упрощает масштабирование приложений и позволяет легко запускать их в любом месте с полной уверенностью в безопасности, производительности, качестве обслуживания и доступности.

>[!Note]
> Чтобы скачать Windows Server, см. статью [Ознакомительные версии Windows Server](https://www.microsoft.com/evalcenter/evaluate-windows-server-technical-preview).

Windows Server 2016 добавляет следующие новые технологии сетевого взаимодействия:

- Программно-конфигурируемая сеть: Сетевой контроллер обеспечивает централизованную программируемую точку автоматизации для управления, настройки, мониторинга, а также выявления и устранения неисправностей в виртуальной и физической сетевой инфраструктуре центра данных. Сетевой контроллер позволяет использовать виртуализацию сетевых функций, как легко развернуть виртуальные машины \(виртуальных машин\) для балансировки нагрузки программного обеспечения \(SLB\) позволяет оптимизировать сетевой трафик, загружает для клиентов и удаленного доступа Шлюзы, чтобы предоставить клиентам возможности подключения, они должны между Интернетом, локальных и облачных ресурсов. Сетевой контроллер также можно использовать для управления брандмауэром центра обработки данных на виртуальных машинах и узлах Hyper-V.

- Платформа сети: С помощью новых функций для существующих технологий сетевой платформы, можно использовать политики DNS для настройки сервера ответов на запросы DNS, используйте со схождением сетевой КАРТЫ, что дескрипторы вместе удаленный доступ к памяти \(RDMA\) трафик Ethernet и , используйте Switch Embedded Teaming \(ЗАДАТЬ\) для создания виртуальных коммутаторов Hyper-V подключен к сетевые платы RDMA и использовать управление IP-адресами \(IPAM\) для управления зонами DNS и серверы, а также DHCP и IP-адреса.

Дополнительные сведения см. в разделе [Поддерживаемые сценарии сетевого взаимодействия в Windows Server](windows-server-supported-networking-scenarios.md).

В следующих разделах представлены сведения о технологиях SDN и сетевой платформы.

## <a name="software-defined-networking-technologies"></a>Технологии программно-конфигурируемых сетей

### <a name="software-defined-networking-40sdn41sdnsoftware-defined-networkingmd"></a>[Программно-конфигурируемой сети &#40;SDN&#41;](sdn/software-defined-networking.md)

Этот раздел поможет получить представление о технологиях программно-конфигурируемых сетей, входящих в состав Windows Server System Center и Microsoft Azure.

>[!NOTE]
>Для узлов Hyper-V и виртуальных машин \(виртуальных машин\) запуска серверов инфраструктуры SDN, такие как узлы сетевого контроллера и балансировка нагрузки программного обеспечения, необходимо установить Windows Server 2016 Datacenter edition. Для Hyper-V, которые содержат только узлы клиента нагрузки виртуальных машин, подключенных к SDN\-управляемой сети, можно запустить Windows Server 2016 Standard edition.

### <a name="deploy-a-software-defined-network-infrastructure-using-scriptssdndeploydeploy-a-software-defined-network-infrastructure-using-scriptsmd"></a>[Развертывание инфраструктуры программно-определяемой сети с помощью сценариев](sdn/deploy/Deploy-a-Software-Defined-Network-infrastructure-using-scripts.md)
Это руководство содержит инструкции по развертыванию сетевого контроллера с виртуальными сетями и шлюзами в тестовой лабораторной среде.

### <a name="network-controllersdntechnologiesnetwork-controllernetwork-controllermd"></a>[Сетевой контроллер](sdn/technologies/network-controller/Network-Controller.md)

Сетевой контроллер обеспечивает централизованную программируемую точку автоматизации для управления, настройки, мониторинга, а также выявления и устранения неисправностей в виртуальной и физической сетевой инфраструктуре центра данных.

### <a name="software-load-balancing-40slb41-for-sdnsdntechnologiesnetwork-function-virtualizationsoftware-load-balancing-for-sdnmd"></a>[Программная Балансировка нагрузки &#40;SLB&#41; для SDN](sdn/technologies/network-function-virtualization/software-load-balancing-for-sdn.md)

Поставщики облачных служб \(CSP\) и предприятия, развертывающие программно определяемой сети (SDN) в Windows Server 2016 можно использовать балансировку нагрузки программного обеспечения \(SLB\) для равномерного распределения клиента и клиента клиент сетевого трафика между ресурсами виртуальной сети. Windows Server SLB позволяет размещать одну и ту же рабочую нагрузку на нескольких серверах, что обеспечивает высокий уровень доступности и масштабирование.

### <a name="ras-gateway-for-sdnsdntechnologiesnetwork-function-virtualizationras-gateway-for-sdnmd"></a>[Шлюз RAS](sdn/technologies/network-function-virtualization/RAS-Gateway-for-SDN.md)

Шлюз RAS, который находится на базе программного обеспечения, мультитенантную систему, протокол BGP \(BGP\) маршрутизатор с поддержкой в Windows Server 2016 предназначен для поставщиков облачных служб \(CSP\) и предприятий, которые размещают несколько виртуальных сетей клиента с помощью виртуализации сети Hyper-V. 

### <a name="network-function-virtualizationsdntechnologiesnetwork-function-virtualizationnetwork-function-virtualizationmd"></a>[Виртуализация сетевых функций](sdn/technologies/network-function-virtualization/Network-Function-Virtualization.md)

В центрах обработки данных программно, сетевые функции, выполняемые аппаратными устройствами \(такие как подсистемы балансировки нагрузки, брандмауэры, маршрутизаторы, коммутаторы и т. д.\) , все чаще виртуализируются в виде виртуальных устройств. Такая "виртуализация сетевых функций" является естественным этапом развития виртуализации серверов и сетей.

### <a name="datacenter-firewall-overviewsdntechnologiesnetwork-function-virtualizationdatacenter-firewall-overviewmd"></a>[Обзор брандмауэра центра обработки данных](sdn/technologies/network-function-virtualization/Datacenter-Firewall-Overview.md)

Брандмауэр центра обработки данных —брандмауэр сетевого уровня с пятью кортежами (протокол, номера начального и конечного портов, начальный и конечный IP-адреса), с функцией отслеживания состояния и поддержкой нескольких клиентов.

## <a name="bkmk_networking"></a>Технологии сетевого взаимодействия

Приведенная ниже таблица содержит ссылки на некоторые технологии сетевого взаимодействия в Windows Server 2016.

### <a name="whats-new-in-networkingnetworkingwhat-s-new-in-networkingmd"></a>[Новые возможности сетевых технологий](../networking/What-s-New-in-Networking.md)

Прочитайте следующие разделы, чтобы ознакомиться с новыми сетевыми технологиями и новыми функциями для существующих технологий в Windows Server 2016.

### <a name="branchcachebranchcachebranchcachemd"></a>[BranchCache](branchcache/BranchCache.md)

BranchCache — это глобальная сеть \(глобальной сети\) технология оптимизации пропускной способности. Для оптимизации пропускной способности глобальной сети служба BranchCache получает данные с серверов содержимого в главном офисе или облаке и помещает их в кэш на компьютерах филиала, когда пользователи получают доступ к содержимому на удаленных серверах, что позволяет обеспечить для клиентских компьютеров в филиалах локальный доступ к данным вместо доступа по глобальной сети.

### <a name="core-network-guide-for-windows-server-2016core-network-guidecore-network-guide-windows-servermd"></a>[Руководство по основной сети для Windows Server 2016](core-network-guide/core-network-guide-windows-server.md)

Узнайте, как развернуть сеть Windows Server с помощью руководства по основной сети, а также добавить компоненты в сетевое развертывание с помощью вспомогательных руководств по основной сети.

### <a name="directaccessremoteremote-accessdirectaccessdirectaccessmd"></a>[DirectAccess](../remote/remote-access/directaccess/DirectAccess.md)

DirectAccess предоставляет удаленным пользователям возможность подключения к сетевым ресурсам организации. 

Документация DirectAccess теперь находится в разделе [Удаленный доступ и управление серверами](https://docs.microsoft.com/windows-server/remote/) оглавления Windows Server 2016 в разделе [Удаленный доступ](https://docs.microsoft.com/windows-server/remote/remote-access/remote-access). Дополнительные сведения см. в разделе [DirectAccess](../remote/remote-access/directaccess/DirectAccess.md).

### <a name="domain-name-system-40dns41dnsdns-topmd"></a>[Служба доменных имен &#40;DNS&#41;](dns/dns-top.md)

Служба доменных имен \(DNS\) представляет собой один из стандартных в отрасли наборов протоколов, реализующих взаимодействие TCP/IP, а DNS-клиент и DNS-сервер совместно предоставляют службы разрешения имен при сопоставлении имен с IP-адресами для компьютеров и пользователей.

### <a name="dynamic-host-configuration-protocol-40dhcp41technologiesdhcpdhcp-topmd"></a>[Dynamic Host Configuration Protocol &#40;DHCP&#41;](technologies/dhcp/dhcp-top.md)

Dynamic Host Configuration Protocol \(DHCP\) — это протокол клиент сервер, который автоматически обеспечивает протокол Интернета \(IP-адрес\) узел с его IP-адрес и другие связанные сведения о конфигурации, такие как подсеть маска и шлюз по умолчанию.

### <a name="hyper-v-network-virtualizationsdntechnologieshyper-v-network-virtualizationhyper-v-network-virtualizationmd"></a>[Виртуализация сети Hyper-V](sdn/technologies/hyper-v-network-virtualization/Hyper-V-Network-Virtualization.md)

Виртуализация сети Hyper-V \(HNV\) обеспечивает виртуализацию сетей клиентов на основе общей физической сетевой инфраструктуры.

### <a name="hyper-v-virtual-switchvirtualizationhyper-v-virtual-switchhyper-v-virtual-switchmd"></a>[Виртуальный коммутатор Hyper-V](../virtualization/hyper-v-virtual-switch/Hyper-V-Virtual-Switch.md)

Виртуальный коммутатор Hyper-V — это программный сетевой коммутатор Ethernet уровня 2, который доступен в диспетчере Hyper-V при установке роли сервера Hyper-V. Коммутатор предоставляет программно управляемые и расширяемые возможности для подключения виртуальных машин к виртуальным сетям и к физической сети. Виртуальный коммутатор Hyper-V также обеспечивает применение политик в области безопасности, изоляции и уровней обслуживания. 

Документация по виртуальному коммутатору Hyper-V теперь находится в разделе **Виртуализация** оглавления Windows Server 2016. Дополнительные сведения см. в разделе [Виртуальный коммутатор Hyper-V](../virtualization/hyper-v-virtual-switch/Hyper-V-Virtual-Switch.md).

### <a name="ip-address-management-40ipam41technologiesipamipam-topmd"></a>[Управление IP-адресами &#40;IPAM&#41;](technologies/ipam/ipam-top.md)

Управление IP-адресами \(IPAM\) — это встроенный набор инструментов для сквозного планирования, развертывания, администрирования и отслеживания инфраструктуры IP-адресов в многофункциональном пользовательском интерфейсе. IPAM автоматически обнаруживает серверы инфраструктуры IP-адресов и доменных имен \(DNS\) серверов в сети и позволяет управлять ими из центрального интерфейса.

### <a name="network-load-balancingtechnologiesnetwork-load-balancingmd"></a>[Балансировка сетевой нагрузки](technologies/Network-Load-Balancing.md)

Балансировка сетевой нагрузки \(NLB\) распределяет трафик между несколькими серверами, используя сетевой протокол TCP/IP. Для развертываний отличных от SDN, NLB обеспечивает без учета состояния приложения, такие как веб-серверов под управлением Internet Information Services \(IIS\), путем добавления дополнительных серверов по мере увеличения нагрузки.

### <a name="high-performance-networkingtechnologieshpnhpn-topmd"></a>[Высокой производительности сети](technologies/hpn/hpn-top.md)

К технологиям разгрузки и оптимизации сети в Windows Server 2016 относятся возможности и технологии Software Only (SO), интегрированные возможности и технологии Software and Hardware (SH), а также возможности и технологии Hardware Only (HO).

Кроме того, доступна следующая документация по технологиям разгрузки и оптимизации.

- [Руководство по настройке сети со схождением интерфейс карты (NIC)](technologies/conv-nic/cnic-top.md)
- [Мост центра обработки данных](technologies/dcb/dcb-top.md)
- [Виртуального масштабирования на стороне приема (vRSS)](technologies/vrss/vrss-top.md)


### <a name="network-policy-servertechnologiesnpsnps-topmd"></a>[Сервер политики сети](technologies/nps/nps-top.md)

Сервер сетевых политик (NPS) позволяет создавать и применять политики доступа к сети на уровне организации для проверки подлинности и авторизации сетевых подключений.

### <a name="network-shell-netshtechnologiesnetshnetshmd"></a>[Сетевой оболочки (Netsh)](technologies/netsh/netsh.md)

Можно использовать сетевой оболочки \(netsh\) сети служебная программа для сетевых технологий в Windows Server 2016 и Windows 10.

### <a name="network-subsystem-performance-tuningtechnologiesnetwork-subsystemnet-sub-performance-topmd"></a>[Производительности сетевой подсистемы помощник по настройке](technologies/network-subsystem/net-sub-performance-top.md)

Этот раздел содержит сведения о выборе правильного сетевого адаптера для рабочей нагрузки сервера, порядок сетевых интерфейсов, счетчики производительности, связанные с сетью, и настройка производительности сетевых адаптеров и связанных сетевых технологий, таких как Масштабирование на стороне приема \(RSS\), получать объединения со значением на стороне \(RSC\)и другие.

### <a name="nic-teamingtechnologiesnic-teamingnic-teamingmd"></a>[Объединение Сетевых карт](technologies/nic-teaming/NIC-Teaming.md)

Объединение сетевых карт позволяет сгруппировать физические сетевые адаптеры Ethernet в один или несколько программных виртуальных сетевых адаптеров. Эти виртуальные сетевые адаптеры обеспечивают высокую производительность и отказоустойчивость в случае сбоя сетевого адаптера.

### <a name="quality-of-service-qos-policytechnologiesqosqos-policy-topmd"></a>[Политики качества обслуживания (QoS)](technologies/qos/qos-policy-top.md)

Вы можете использовать политику качества обслуживания как централизованное средство управления пропускной способностью сети для всей инфраструктуры Active Directory, создавая профили качества обслуживания, параметры которых распространяются с помощью групповой политики.

### <a name="remote-accessremoteremote-accessremote-accessmd"></a>[Удаленный доступ](../remote/remote-access/remote-access.md)

Можно использовать технологии удаленного доступа, такие как DirectAccess и виртуальные частные сети \(VPN\) для предоставления удаленным работникам с подключением к ресурсам внутренней сети. Кроме того, можно использовать удаленный доступ для локальной сети \(LAN\) маршрутизации и для прокси веб-приложения. Он предоставляет функции обратного прокси-сервера для веб-приложений в корпоративной сети, что делает их доступными для пользователей с любых устройств из-за пределов корпоративной сети.

Документация по удаленному доступа теперь находится в разделе [Удаленный доступ и управление серверами](https://docs.microsoft.com/windows-server/remote/) оглавления Windows Server 2016. Дополнительные сведения см. в разделе [Удаленный доступ](../remote/remote-access/remote-access.md).

Дополнительные сведения о прокси-сервере веб-приложения, который является службой роли сервера удаленного доступа, см. в разделе [Прокси-сервер веб-приложений в Windows Server 2016](https://docs.microsoft.com/windows-server/remote/remote-access/web-application-proxy/web-application-proxy-windows-server).

### <a name="virtual-private-networking-vpnremoteremote-accessvpnvpn-topmd"></a>[Виртуальные частные сети (VPN)](../remote/remote-access/vpn/vpn-top.md)

В Windows Server 2016 **DirectAccess и VPN** являются службой роли в **роли сервера удаленного доступа**.

Во время установки удаленного доступа в качестве VPN-сервера, можно использовать виртуальные частные сети \(VPN\) для предоставления удаленных сотрудников с подключением к сети организации через Интернет -, одновременно сохраняя сведения конфиденциальности с помощью зашифрованного соединения.

При использовании VPN удаленного доступа Windows Server 2016 (и клиентских компьютеров с Windows 10) вы можете развернуть постоянно подключенный VPN-профиль. Такой вид VPN позволяет управлять удаленными клиентами VPN, которые всегда подключены, а также обеспечивает удобные условия работы для удаленных сотрудников, которым больше не нужно вручную подключаться и отключаться из VPN к сети вашей организации.

Дополнительные сведения см. в разделе [Руководство по развертыванию постоянно подключенной сети VPN удаленного доступа для Windows Server 2016 и Windows 10](https://docs.microsoft.com/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/always-on-vpn-deploy).

>[!NOTE]
>Документация по VPN теперь находится в разделе [Удаленный доступ и управление серверами](https://docs.microsoft.com/windows-server/remote/) оглавления Windows Server 2016 в разделе [Удаленный доступ](https://docs.microsoft.com/windows-server/remote/remote-access/remote-access).

Дополнительные сведения о VPN см. в разделе [Виртуальная частная сеть (VPN)](https://docs.microsoft.com/windows-server/remote/remote-access/vpn/vpn-top).

### <a name="windows-container-networkinghttpsdocsmicrosoftcomvirtualizationwindowscontainersmanage-containerscontainer-networking"></a>[Сетевые подключения контейнеров Windows](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/container-networking)

Сетевые подключения контейнеров Windows позволяют создавать и контролировать сети ими для подключения конечных точек контейнеров на узлах Windows 10 и Windows Server с помощью стандартных средств и рабочих процессов. Сетевые подключения контейнеров Windows поддерживают несколько топологий, такие как частные, плоские уровня 2 и маршрутизируемые уровня 3.

Также поддерживаются наложения, можно создать локально на узле с помощью Docker, Kubernetes или Windows PowerShell через подключаемые модули, взаимодействовать со службой Windows Networking узла \(HNS\). Вы можете создать и управлять несколькими\-сетей кластера узла через выше уровня оркестрации системы путем взаимодействия через локальный агент на каждом узле HNS.

### <a name="windows-internet-name-service-winstechnologieswinswins-topmd"></a>[Windows Internet Name Service (WINS)](technologies/wins/wins-top.md)

WINS — это традиционная служба регистрации и разрешения имен компьютеров, которая сопоставляет NetBIOS-имена компьютеров с IP-адресами. Рекомендуется использовать службу DNS вместо WINS.

## <a name="additional-resources"></a>Дополнительные ресурсы

Сетевые ресурсы для операционных систем более ранних версий, чем Windows Server 2016, доступны в следующих расположениях.

- [Обзор сетевого взаимодействия](https://technet.microsoft.com/library/hh831357.aspx) в Windows Server 2012 и Windows Server 2012 R2
- [Возможности работы с сетями](https://technet.microsoft.com/library/cc753940) в Windows Server 2008 и Windows Server 2008 R2
- Windows Server 2003 [Устаревший контент Windows Server 2003/2003 R2](https://www.microsoft.com/download/details.aspx?id=53314)
