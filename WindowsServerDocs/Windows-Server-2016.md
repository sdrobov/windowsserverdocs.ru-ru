---
redirect_url: /windows-server/windows-server
ms.openlocfilehash: 9ef5565af748b4dd592e71ec4bd34a2be58003d9
ms.sourcegitcommit: 3a3d62f938322849f81ee9ec01186b3e7ab90fe0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2020
ms.locfileid: "75947295"
---
# <a name="windows-server-2016"></a>Windows Server 2016

Эта библиотека содержит информацию, необходимую ИТ-специалистам для оценки, планирования, развертывания, защиты и администрирования Windows Server 2016.

> [!Note] 
> В следующую версию Windows Server будут внесены изменения! Информацию о планируемых изменениях см. в [обзоре Semi-Annual Channel для Windows Server](./get-started/semi-annual-channel-overview.md). 

[![Видеообзор Windows Server 2016](media/front-page-video.png)](https://www.youtube-nocookie.com/embed/V8oF0JpDzaM)

<table border="0" width="100%" align='center'>
  <tr style="text-align:center;">
    <td align='center' style="width:25%; border:0;">
      <a href="/windows-server/get-started/what-s-new-in-windows-server-2016"> &lt;img height=145 src=&quot;media/whats-new-highlight.png&quot; alt=&quot;What&#39;s new icon&quot; title=&quot;Whats new in Windows Server 16?&quot;/&gt;</a>
        <br/>Что нового?
    </td>
    <td align='center' style="width:25%; border:0;">
      <a href="/windows-server/get-started/server-basics"> &lt;img height=145 src=&quot;media/1-getstarted.png&quot; alt=&quot;get started icon&quot; title=&quot;Get Started with Windows Server 16&quot; /&gt;</a>
      <br/>Приступая к работе </td>
    <td align='center' style="width:25%; border:0;">
      <a href="/windows-server/administration/index"> &lt;img height=145 src=&quot;media/8-management.png&quot; alt=&quot;administer icon&quot; title=&quot;Administer Windows Server&quot; /&gt;</a>
      <br/>Администрирование </td>
    <td align='center' style="width:25%; border:0;">
      <a href="/windows-server/failover-clustering/failover-clustering-overview"> &lt;img height=145 src=&quot;media/3-failover.png&quot; alt=&quot;Failover clustering icon&quot; title=&quot;Windows Server Failover clustering&quot; /&gt;</a>
      <br/>Отказоустойчивая кластеризация </td>
  </tr>
  <tr style="text-align:center;">
    <td align='center' style="width:25%; border:0;"><br/>
      <a href="/windows-server/identity/identity-and-access"> &lt;img height=145 src=&quot;media/4-identity.png&quot; alt=&quot;Identity and access icon&quot; title=&quot;Windows Server Identity and Access&quot; /&gt;</a>
      <br>Удостоверение и доступ </td>
    <td align='center' style="width:25%; border:0;"><br/>
      <a href="/windows-server/networking/networking"> &lt;img height=145 src=&quot;media/6-networking.png&quot; alt=&quot;Networking icon&quot; title=&quot;Windows Server Networking&quot; /&gt; </a>
      <br/>сеть; </td>
    <td align='center' style="width:25%; border:0;"><br/>
      <a href="/windows-server/remote/index"> &lt;img height=145 src=&quot;media/remote.png&quot; alt=&quot;remote icon&quot; title=&quot;Remote access and server management&quot; /&gt; </a>
      <br/>Удаленный доступ </td>
    <td align='center' style="width:25%; border:0;"><br/>
      <a href="/windows-server/security/security-and-assurance"> &lt;img height=145 src=&quot;media/5-security.png&quot; alt=&quot;Security icon&quot; title=&quot;Windows Server Security and Assurance&quot; /&gt; </a>
      <br/>Безопасность и контроль </td>
  </tr>
  <tr style="text-align:center;">
    <td align='center' style="width:25%; border:0;">&nbsp;</td>
    <td align='center' style="width:25%; border:0;"><br>
      <a href="/windows-server/storage/storage"> &lt;img height=145 src=&quot;media/7-storage.png&quot; alt=&quot;Storage icon&quot; title=&quot;Windows Server Storage&quot; /&gt; </a>
      <br/>Хранение </td>
   <td align='center' style="width:25%; border:0;"><br/>
      <a href="/windows-server/virtualization/virtualization"> &lt;img height=145 src=&quot;media/virtualization.png&quot; alt=&quot;virtualization icon&quot; title=&quot;Windows Server Virtualization&quot; /&gt;</a>
      <br/>Виртуализация </td>
    <td align='center' style="width:25%; border:0;">[https://blogs.technet.microsoft.com/askperf/2008/11/18/disabling-unnecessary-services-a-word-to-the-wise/](&nbsp;) </td>
  </tr>
</table>

<br/>

> [!Note] 
> Чтобы лично оценить новые функции и возможности в Windows Server 2016, можно скачать ознакомительную версию, посетив страницу [Оценки Windows Server](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016). 


## <a name="windows-server-2016-editions"></a>Выпуски Windows Server 2016

Для Windows Server 2016 доступны выпуски Standard, Datacenter и Essentials. Windows Server 2016 Datacenter включает неограниченные права на виртуализацию, а также новые возможности для создания программно-определяемого центра обработки данных. Windows Server 2016 Standard предлагает возможности корпоративного класса с ограниченными правами на виртуализацию. Windows Server Essentials — оптимальный вариант для первого сервера, подключенного к облаку. Он снабжен собственной [подробной документацией](https://go.microsoft.com/fwlink/?LinkID=827171), поэтому в данных материалах основное внимание уделяется выпускам Standard и Datacenter. В следующей таблице кратко перечислены основные различия между выпусками Standard и Datacenter:

|Функция|Datacenter|Standard|  
|-------------------|----------|-----------------------|  
|Основные функциональные возможности Windows Server| да| да|
|Контейнеры Hyper-V/ОС|без ограничений|   2|
|Контейнеры Windows Server|без ограничений|   без ограничений|
|Служба защиты узла| да| да|
|Вариант установки Nano Server| да| да|
|Компоненты хранилища, включая локальные дисковые пространства и реплики хранилища| да| нет|
|Экранированные виртуальные машины| да| нет|
|Инфраструктура программно-конфигурируемой сети (сетевой контроллер, балансировка нагрузки программного обеспечения и мультитенантный шлюз)| да| нет|

Дополнительные сведения см. в статьях [Цены и условия лицензирования для Windows Server 2016](https://www.microsoft.com/cloud-platform/windows-server-pricing) и [Сравнение функций в разных версиях Windows Server](https://www.microsoft.com/cloud-platform/windows-server-comparison).

## <a name="installation-options"></a>Параметры установки

Выпуски Standard и Datacenter поддерживают три варианта установки:

- **Основные серверные компоненты**: сокращает требования к свободному пространству на диске, уменьшает поле для потенциальных атак и, самое главное, снижает требования к обслуживанию. Это **рекомендуемый** вариант, если только у вас нет особой необходимости в дополнительных элементах пользовательского интерфейса и графических средствах управления.
- **Сервер с рабочим столом**: устанавливает стандартный пользовательский интерфейс и все инструменты, в том числе компоненты взаимодействия с пользователем, для которых в выпуске в Windows Server 2012 R2 требовалась отдельная установка. Роли и компоненты сервера устанавливаются при помощи диспетчера серверов или других методов.
- **Nano Server**: это удаленно управляемая серверная ОС, оптимизированная для частных облаков и центров обработки данных. Этот вариант аналогичен Windows Server в режиме основных серверных компонентов, однако значительно меньше по размеру, не имеет функций локального входа и поддерживает только 64-разрядные приложения, средства и агенты. В сравнении с другими вариантами он занимает гораздо меньше места на диске, намного быстрее запускается и требует на порядок меньше обновлений и перезапусков.

>[!Note]
> В отличие от предыдущих выпусков Windows Server, после установки преобразовать основные серверные компоненты в сервер с возможностями рабочего стола (и наоборот) невозможно. Например, если вы установили основные серверные компоненты, а затем решили использовать сервер с возможностями рабочего стола, необходимо выполнить установку заново (и наоборот).


Теперь, когда вы знаете, какой выпуск и вариант установки подходит именно вам, щелкните ниже для начала работы с Windows Server 2016.
<br/>
<br/>

<table border="0" width="100%" align='center'>
  <tr style="text-align:center;">
    <td align='center' style="width:33%; border:0;">
      <a  href="/windows-server/get-started/getting-started-with-nano-server"> <img width="175" src="media/nano.png" alt="Icon representing Nano server" title="Сервер Nano Server — самое простое решение" /><br/>Nano Server — <br/>самое простое решение</a>
    </td>
    <td align='center' style="width:33%; border:0;"><a href="/windows-server/get-started/getting-started-with-server-core"> <img width="175" src="media/servercore.png" alt="Icon representing the Server Core installation" title="Основные серверные компоненты — рекомендуется" /><br/>Основные серверные компоненты — <br/>рекомендуется</a></td>
   <td align='center' style="width:33%; border:0;"><a href="/windows-server/get-started/getting-started-with-server-with-desktop-experience"><img width="175" src="media/desktop.png" alt="Icon representing the full desktop experience installation option for Windows Server" title="Возможности рабочего стола — все возможности" /><br/>Возможности рабочего стола — <br/>полный интерфейс</a></td>
  </tr>
</table>

## <a name="windows-server-software-defined-datacenter-sddc"></a>Программно-определяемый центр обработки данных (SDDC) Windows Server

Технологии виртуализированного хранилища, сети, системы безопасности и средств управления являются основой программного ЦОД Windows Server.
<br/>
<br/>

<table border="0" width="100%" align='center'>
  <tr style="text-align:center;">
    <td align='center' style="width:10%; border:0;"></td>
    <td align='center' style="width:50%; border:0;"><a href="/windows-server/sddc"><img width="400" src="media/sddc/WS16-heading.png" alt="Icon representing SDDC" title="Программно-определяемый центр обработки данных (SDDC) Windows Server" /><br/>Программно-определяемый центр обработки данных (SDDC) Windows Server</a></td>
    <td align='center' style="width:10%; border:0;"></td>
  </tr>
</table>
