---
title: Программная балансировка нагрузки для SDN
description: С помощью этого раздела можно узнать о программной балансировке нагрузки для программно определенных сетей в Windows Server 2016.
manager: grcusanz
ms.prod: windows-server
ms.technology: networking-sdn
ms.topic: article
ms.assetid: 97abf182-4725-4026-801c-122db96964ed
ms.author: anpaul
author: AnirbanPaul
ms.openlocfilehash: 245faa00eed6f8ee49f8d178ab2cde5d01b1e23e
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80859577"
---
# <a name="software-load-balancing-slb-for-sdn"></a>Программная балансировка нагрузки \(\) SLB для SDN

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

С помощью этого раздела можно узнать о программной балансировке нагрузки для программно определенных сетей в Windows Server 2016.  

Поставщики облачных служб (CSP) и предприятия, которые развертывают программно-определяемую сеть (SDN) в Windows Server 2016, могут использовать программную балансировку нагрузки (SLB) для равномерного распределения сетевого трафика клиентов клиента и клиента между ресурсами виртуальной сети. Windows Server SLB позволяет размещать одну и ту же рабочую нагрузку на нескольких серверах, что обеспечивает высокий уровень доступности и масштабирование.
  
Windows Server SLB включает следующие возможности.  
  
-   Службы балансировки нагрузки уровня 4 (на уровне сервера) для трафика TCP/UDP "Север-Южный" и "Восток-Западная".  
  
-   Общая и внутренняя балансировка нагрузки сетевого трафика.  
  
-   Поддерживает динамические IP-адреса (DIP) в виртуальных локальных сетях (VLAN) и виртуальных сетях, создаваемых с помощью виртуализации сети Hyper-V.  
  
-   Поддержка пробы работоспособности.  
  
-   Все готово к масштабированию в облаке, включая возможности горизонтального масштабирования и возможности увеличения масштаба для мультиплексоров и агентов узлов.  
  
Дополнительные сведения см. в разделе [функции балансировки нагрузки программного обеспечения](#bkmk_features) этой статьи.  
  
> [!NOTE]  
> Мультитенантность для виртуальных ЛС не поддерживается сетевым контроллером, однако вы можете использовать виртуальные ЛС с SLB для управляемых рабочих нагрузок поставщика услуг, таких как инфраструктура центра обработки данных и веб-серверы с высокой плотностью.  
  
С помощью Windows Server SLB можно масштабировать возможности балансировки нагрузки с помощью виртуальных машин SLB на тех же серверах вычислений Hyper-V, которые используются для других рабочих нагрузок виртуальных машин. По этой причине SLB поддерживает быстрое создание и удаление конечных точек балансировки нагрузки, необходимых для операций CSP. Кроме того, Windows Server SLB поддерживает десятки гигабайт на кластер, предоставляет простую модель подготовки и легко масштабируется и в.  
  
**Принцип работы SLB**  
  
SLB работает путем сопоставления виртуальных IP-адресов (VIP) с динамическими IP-адресами (DIP), которые являются частью набора ресурсов облачной службы в центре обработки данных.  
  
VIP — это отдельные IP-адреса, которые обеспечивают общий доступ к пулу виртуальных машин с балансировкой нагрузки. Например, VIP — это IP-адреса, предоставляемые в Интернете, чтобы клиенты и клиентские заказчики могли подключаться к ресурсам клиента в облачном центре обработки данных.  
  
DIP — это IP-адреса виртуальных машин, являющихся членами пула с балансировкой нагрузки, за которым находится виртуальная ЛС. DIP назначаются в облачной инфраструктуре ресурсам клиента.  
  
Виртуальные IP-адреса находятся в мультиплексоре SLB (МУЛЬТИПЛЕКСОРе).  МУЛЬТИПЛЕКСОР состоит из одной или нескольких виртуальных машин.  Сетевой контроллер обеспечивает каждый МУЛЬТИПЛЕКСОР с каждым виртуальным IP-адресом, и каждый МУЛЬТИПЛЕКСОР в свою очередь использует протокол BGP (BGP) для объявления каждого VIP в маршрутизаторах в физической сети в виде маршрута/32.  BGP позволяет физическим сетевым маршрутизаторам:  
  
-   Узнайте, что виртуальный IP-адрес доступен в каждом МУЛЬТИПЛЕКСОРе, даже если мультиплексоров находятся в разных подсетях в сети уровня 3.  
  
-   Распределите нагрузку для каждого доступного виртуального IP-адреса во всех доступных мультиплексоров с помощью маршрутизации с одинаковыми затратами (ECMP).  
  
-   Автоматическое обнаружение сбоя или удаления МУЛЬТИПЛЕКСОРа и прекращение отправки трафика в неисправный МУЛЬТИПЛЕКСОР.  
  
-   Распределите нагрузку от неисправного или удаленного МУЛЬТИПЛЕКСОРа по работоспособному мультиплексоров.  
  
Когда общедоступный трафик поступает из Интернета, МУЛЬТИПЛЕКСОР SLB проверяет трафик, который содержит виртуальный IP-адрес в качестве назначения, а затем сопоставляет и переписывает трафик, чтобы он поступал на отдельный DIP. Для входящего сетевого трафика эта транзакция выполняется в двухэтапный процессе, который разбивается между виртуальными машинами МУЛЬТИПЛЕКСОРа и узлом Hyper-V, где находится целевой DIP-адрес:  
  
-   Балансировка нагрузки. МУЛЬТИПЛЕКСОР использует виртуальный IP-адрес для выбора DIP, инкапсулирует пакет и перенаправляет трафик на узел Hyper-V, где расположен DIP.  
  
-   Преобразование сетевых адресов (NAT). узел Hyper-V удаляет инкапсуляцию из пакета, Преобразует виртуальный IP-адрес в DIP, пересопоставляет порты и перенаправляет пакет на виртуальную машину DIP.  
  
МУЛЬТИПЛЕКСОР знает, как сопоставлять виртуальные IP-адреса с правильными DIP из-за политик балансировки нагрузки, определяемых с помощью сетевого контроллера. Эти правила включают протокол, интерфейсный порт, порт внутренних портов и алгоритм распределения (5, 3 или 2 кортежа).  
  
Когда клиентские виртуальные машины реагируют и отправляют исходящий сетевой трафик обратно в Интернет или удаленные расположения клиента, так как NAT выполняется узлом Hyper-V, трафик обходит МУЛЬТИПЛЕКСОР и переходит непосредственно на пограничные маршрутизаторы с узла Hyper-V. Этот процесс обхода МУЛЬТИПЛЕКСОРа называется прямым возвратом сервера (DSR).  
  
После установления первоначального потока сетевого трафика входящий сетевой трафик полностью обходит МУЛЬТИПЛЕКСОР SLB.  
  
На следующем рисунке клиентский компьютер выполняет запрос DNS для IP-адреса сайта SharePoint компании, в данном случае вымышленной компании Contoso. Выполняется следующий процесс.  
  
-   DNS-сервер возвращает клиенту 107.105.47.60 виртуальной ЛС.  
  
-   Клиент отправляет запрос HTTP к виртуальному IP-адресу.  
  
-   В физической сети доступно несколько путей для достижения виртуального IP-адреса, расположенного в каком-либо МУЛЬТИПЛЕКСОРе.  Каждый маршрутизатор в пути использует ECMP для выбора следующего сегмента контура, пока запрос не поступит в МУЛЬТИПЛЕКСОР.  
  
-   МУЛЬТИПЛЕКСОР, получивший запрос, проверяет настроенные политики и видит наличие двух доступных DIP, 10.10.10.5 и 10.10.20.5 в виртуальной сети для выполнения запроса к виртуальному IP-адресу 107.105.47.60  
  
-   МУЛЬТИПЛЕКСОР выбирает DIP 10.10.10.5 и инкапсулирует пакеты с помощью ВКСЛАН, чтобы он мог отправить его на узел, содержащий DIP, с помощью физического сетевого адреса узла.  
  
-   Узел получает инкапсулированный пакет и проверяет его.  Он удаляет инкапсуляцию и переписывает пакет, так что назначение теперь является DIP 10.10.10.5 вместо виртуального IP-адреса и отправляет трафик в подсеть DIP.  
  
-   Теперь запрос достиг сайта Contoso SharePoint в ферме серверов 2. Сервер создает ответ и отправляет его клиенту, используя собственный IP-адрес в качестве источника.  
  
-   Узел перехватывает исходящий пакет в виртуальном коммутаторе, который запоминает, что клиент (теперь) назначен, сделал исходный запрос к виртуальному IP-адресу.  Узел переписывает источник пакета в виртуальный IP-адрес, чтобы клиент не вижу DIP-адреса.  
  
-   Узел перенаправляет пакет непосредственно в шлюз по умолчанию для физической сети, которая использует стандартную таблицу маршрутизации для пересылки пакета клиенту, который в итоге получает ответ.  
  
![Процесс балансировки нагрузки программного обеспечения](../../../media/Software-Load-Balancing--SLB--for-SDN/slb_process.jpg)  
  
**Внутренний трафик центра обработки данных для балансировки нагрузки**  
  
При балансировке нагрузки сетевого трафика в центре обработки данных, например, между ресурсами клиента, работающими на разных серверах и входящими в одну и ту же виртуальную сеть, виртуальный коммутатор Hyper-V, к которому подключены виртуальные машины, выполняет преобразование сетевых адресов (NAT).  
  
При внутренней балансировке нагрузки трафика первый запрос отправляется и обрабатывается МУЛЬТИПЛЕКСОРом, который выбирает соответствующий DIP-адрес и направляет трафик на DIP. С этого момента установленный поток трафика обходит МУЛЬТИПЛЕКСОР и перейдет непосредственно из ВИРТУАЛЬНОЙ машины в виртуальную машину.  
  
**Зонды работоспособности**  
  
SLB включает пробы работоспособности для проверки работоспособности сетевой инфраструктуры, включая следующие.  
  
-   TCP-зонд к порту  
  
-   HTTP-зонд к порту и URL-адресу  
  
В отличие от традиционного устройства подсистемы балансировки нагрузки, на котором проба поступает на устройстве и передается через сеть на DIP, проба SLB создается на узле, где расположен DIP-адрес, и передается непосредственно от агента узла SLB в DIP, после чего происходит дальнейшая рассылка работа на узлах.  
  
## <a name="software-load-balancing-infrastructure"></a><a name="bkmk_infrastructure"></a>Инфраструктура балансировки нагрузки программного обеспечения  
Чтобы развернуть Windows Server SLB, необходимо сначала развернуть сетевой контроллер в Windows Server 2016 и одну или несколько виртуальных машин МУЛЬТИПЛЕКСОРа SLB.  
  
Кроме того, необходимо настроить узлы Hyper-V с помощью виртуального коммутатора Hyper-V с поддержкой SDN и убедиться, что агент узла SLB запущен.  Маршрутизаторы, обслуживающие узлы, должны поддерживать маршрутизацию с одинаковой ценой (ECMP) и протокол BGP (BGP) и должны быть настроены для приема запросов пиринга BGP от мультиплексоров SLB.  
  
Ниже приведен обзор инфраструктуры SLB.  

![Инфраструктура балансировки нагрузки программного обеспечения](../../../media/Software-Load-Balancing--SLB--for-SDN/slb_overview1.png)  
  
В следующих разделах содержатся дополнительные сведения об этих элементах инфраструктуры SLB.  
  
### <a name="scvmm"></a>SCVMM  
С помощью System Center 2016 можно настроить сетевой контроллер в Windows Server 2016, включая диспетчер SLB и монитор работоспособности. Вы также можете использовать System Center для развертывания SLB Муксс и установки агентов узлов SLB на компьютерах под управлением Windows Server 2016 и Hyper-V.  
  
Дополнительные сведения о System Center 2016 см. в разделе [System center 2016](https://www.microsoft.com/server-cloud/products/system-center-2016/).  
  
> [!NOTE]  
> Если вы не хотите использовать System Center 2016, можно использовать Windows PowerShell или другое приложение управления для установки и настройки сетевого контроллера и инфраструктуры SLB. Дополнительные сведения см. в статье [Развертывание сетевого контроллера с помощью Windows PowerShell](../../../sdn/deploy/Deploy-Network-Controller-using-Windows-PowerShell.md).  
  
### <a name="network-controller"></a>Сетевой контроллер  
Сетевой контроллер размещает диспетчер SLB и выполняет следующие действия для SLB.  
  
-   Обрабатывает команды SLB, которые поставляются через API обмена из System Center, Windows PowerShell или другого приложения управления сетью.  
  
-   Вычисляет политику для распространения на узлах Hyper-V и SLB мультиплексоров.  
  
-   Предоставляет состояние работоспособности инфраструктуры SLB.  
  
### <a name="slb-mux"></a>МУЛЬТИПЛЕКСОР SLB  
МУЛЬТИПЛЕКСОР SLB обрабатывает входящий сетевой трафик и сопоставляет VIP с DIP, а затем перенаправляет трафик на правильный DIP. Каждый МУЛЬТИПЛЕКСОР также использует BGP для публикации маршрутов виртуальных IP-адресов на пограничных маршрутизаторах. Служба "Проверка активности BGP" уведомляет мультиплексоров, когда происходит сбой МУЛЬТИПЛЕКСОРа, что позволяет активному мультиплексоров распространять нагрузку в случае сбоя МУЛЬТИПЛЕКСОРа, по сути обеспечивая балансировку нагрузки для подсистем балансировки нагрузки.  
  
### <a name="hosts-that-are-running-hyper-v"></a>Узлы, работающие под управлением Hyper-V  
SLB можно использовать с компьютерами, работающими под управлением Windows Server 2016 и Hyper-V. Виртуальные машины на узле Hyper-V могут работать под управлением любой операционной системы, поддерживаемой Hyper-V.  
  
### <a name="slb-host-agent"></a>Агент узла SLB  
При развертывании SLB необходимо использовать System Center, Windows PowerShell или другое приложение управления для развертывания агента узла SLB на каждом компьютере узла Hyper-V. Агент узла SLB можно установить во всех версиях Windows Server 2016, обеспечивающих поддержку Hyper-V, включая Nano Server.  
  
Агент узла SLB прослушивает обновления политики SLB с сетевого контроллера. Кроме того, агент узла программирует правила для SLB в виртуальные коммутаторы Hyper-V с поддержкой SDN, настроенные на локальном компьютере.  
  
### <a name="sdn-enabled-hyper-v-virtual-switch"></a>В SDN включен виртуальный коммутатор Hyper-V  
Чтобы виртуальный коммутатор был совместим с SLB, необходимо использовать диспетчер виртуальных коммутаторов Hyper-V или команды Windows PowerShell для создания коммутатора, после чего необходимо включить платформу Virtual Filtering Platform (VFP) для виртуального коммутатора.  
  
Сведения о включении VFP в виртуальных коммутаторах см. в разделе команды Windows PowerShell [Get-вмсистемсвитчекстенсион](https://technet.microsoft.com/library/hh848603.aspx) и [Enable-вмсвитчекстенсион](https://technet.microsoft.com/library/hh848541.aspx?f=255&MSPPError=-2147217396).  
  
Виртуальный коммутатор с включенным SDN Hyper-V выполняет следующие действия для SLB.  
  
-   Обрабатывает путь к данным для SLB.  
  
-   Получает входящий сетевой трафик от МУЛЬТИПЛЕКСОРа.  
  
-   Обходит МУЛЬТИПЛЕКСОР для исходящего сетевого трафика, отправляя его маршрутизатору с помощью коммутатора DSR.  
  
-   Выполняется на экземплярах Hyper-V Nano Server.  
  
### <a name="bgp-enabled-router"></a>Маршрутизатор с поддержкой BGP  
Маршрутизатор BGP выполняет следующие действия для SLB.  
  
-   Направляет входящий трафик в МУЛЬТИПЛЕКСОР с помощью ECMP.  
  
-   Для исходящего сетевого трафика использует маршрут, предоставленный узлом.  
  
-   Прослушивает обновления маршрутов для виртуальных IP-адресов МУЛЬТИПЛЕКСОРа SLB.  
  
-   Удаляет мультиплексоров SLB из вращения SLB в случае сбоя проверки активности.  
  
## <a name="software-load-balancing-features"></a><a name="bkmk_features"></a>Функции балансировки нагрузки программного обеспечения  
Ниже приведены некоторые функции и возможности SLB.  
  
**Основные функциональные возможности**  
  
-   SLB предоставляет службы балансировки нагрузки уровня 4 для трафика TCP/UDP "Север-Южный" и "Восток-Западная"  
  
-   SLB можно использовать в сети на основе виртуализации Hyper-V.  
  
-   SLB можно использовать с сетью на основе виртуальной ЛС для DIP-переключателей, подключенных к виртуальному коммутатору Hyper-V с поддержкой SDN.  
  
-   Один экземпляр SLB может обслуживать несколько клиентов  
  
-   SLB и DIP поддерживают масштабируемый путь с низкой задержкой, реализованный прямым возвратом сервера (DSR).  
  
-   Функции SLB при использовании объединения коммутаторов (SET) или виртуализации ввода-вывода с одним корневым каталогом (SR-IOV)  
  
-   SLB включает поддержку протокола Интернета версии 4 (IPv4)  
  
-   Для сценариев шлюза типа "сеть — сеть" SLB предоставляет функции NAT, позволяющие всем подключениям типа "сеть — сеть" использовать один общедоступный IP-адрес.  
  
-   Можно установить SLB, включая агент узла и МУЛЬТИПЛЕКСОР, на Windows Server 2016, Full, Core и Nano install.  
  
**Масштабирование и производительность**  
  
-   Все готово к масштабированию в облаке, включая масштабирование и возможность увеличения масштаба для мультиплексоров и агентов узлов.  
  
-   Один модуль сетевого контроллера диспетчера SLB может поддерживать 8 экземпляров МУЛЬТИПЛЕКСОРа  
  
**Высокая доступность**  
  
-   Можно развернуть SLB на более чем 2 узлах в конфигурации "активный/активный"  
  
-   Мультиплексоров можно добавлять и удалять из пула МУЛЬТИПЛЕКСОРа, не влияя на службу SLB. Это обеспечивает доступность SLB при   
    отдельные мультиплексоров обновляются.  
  
-   Время доступности отдельных экземпляров МУЛЬТИПЛЕКСОРа составляет 99%  
  
-   Данные мониторинга работоспособности доступны для сущностей управления  
  
**Выравнивание**  
  
-   Вы можете развернуть и настроить SLB с помощью SCVMM.  
  
-   SLB обеспечивает одноклиентскую единую границу путем легкого интеграции с такими устройствами Майкрософт, как многоклиентский шлюз RAS, брандмауэр центра обработки данных и отражатель маршрутизации.  
  

