---
title: Новые возможности Windows Server 2019
description: В этой статье приведен обзор новых возможностей Windows Server 2019, включая возможности рабочего стола, службу миграции хранилища, системную аналитику, сетевой адаптер Azure, улучшения Локальных дисковых пространств и другие изменения.
ms.prod: windows-server
ms.technology: server-general
ms.topic: article
author: jasongerend
ms.author: jgerend
ms.localizationpriority: high
ms.date: 06/04/2019
ms.openlocfilehash: fd094347679d147a04faefdf3741a06addda2026
ms.sourcegitcommit: 78b59522234825c43b00c271a04c35f3fd9d65e3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86946582"
---
# <a name="whats-new-in-windows-server-2019"></a>Новые возможности Windows Server 2019

> Применяется к: Windows Server 2019

В этом разделе описаны некоторые новые функции Windows Server 2019. В основе операционной системы Windows Server 2019 лежит надежная платформа Windows Server 2016. Она предоставляет множество инновационных возможностей для работы с четырьмя основными областями: гибридное облако, безопасность, платформа приложений и гиперконвергентная инфраструктура (HCI).

Описание новых возможностей выпусков Windows Server Semi-Annual Channel см. в статье [What's new in Windows Server](../get-started/whats-new-in-windows-server.md) (Новые возможности Windows Server).

## <a name="general"></a>Общие

### <a name="windows-admin-center"></a>Windows Admin Center

Windows Admin Center представляет собой локально развертываемое браузерное приложение для управления серверами, кластерами, гиперконвергентной инфраструктурой и ПК под управлением Windows 10. Оно поставляется без дополнительной платы в составе Windows и готово для использования в рабочей среде.

Вы можете установить Windows Admin Center в Windows Server 2019, а также в Windows 10 и более ранних версиях Windows и Windows Server, и использовать это решение для управления серверами и кластерами с Windows Server 2008 R2 и более поздних версий.

Подробные сведения см. в статье [Hello, Windows Admin Center!](../manage/windows-admin-center/overview.md) (Привет, Windows Admin Center!).

### <a name="desktop-experience"></a>Возможности рабочего стола

Поскольку Windows Server 2019 — это выпуск Long-Term Servicing Channel (LTSC), он включает <b>возможности рабочего стола</b>. (Выпуски Semi-Annual Channel \(SAC\) не включают возможности рабочего стола по умолчанию. Они представляют собой исключительно выпуски образа контейнеров основных серверных компонентов и сервера Nano Server.) Как и в случае с Windows Server 2016, во время настройки операционной системы вы можете выбрать установку основных серверных компонентов или установку сервера с возможностями рабочего стола.

### <a name="system-insights"></a>Системная аналитика

Системная аналитика — это новая функция, доступная в Windows Server 2019, за счет которой в Windows Server реализуется встроенная поддержка локальных возможностей прогнозной аналитики. Эти возможности прогнозирования, каждая из которых основана на модели машинного обучения, выполняют локальный анализ системных данных Windows Server, например счетчиков производительности и событий, предоставляя аналитические сведения о работе ваших серверов, а также помогают сократить эксплуатационные затраты, связанные с активным управлением проблемами в развертываниях Windows Server.

## <a name="hybrid-cloud"></a>Гибридное облако

### <a name="server-core-app-compatibility-feature-on-demand"></a>Функция совместимости приложений основных серверных компонентов по требованию

[Функция совместимости приложений основных серверных компонентов по требованию (FOD)](./install-fod-19.md) значительно улучшает совместимость приложений для установки основных серверных компонентов Windows путем включения подмножества двоичных файлов и компонентов из Windows Server с возможностями рабочего стола без добавления самой графической среды возможностей рабочего стола Windows Server.  Это делается для расширения функциональных возможностей и улучшения совместимости основных серверных компонентов практически без усложнения процесса их установки.  

Эта дополнительная функция по требованию доступна в отдельном ISO-файле, и ее можно добавлять только в образы и установки основных серверных компонентов Windows с помощью DISM. 

## <a name="security"></a>Безопасность

### <a name="windows-defender-advanced-threat-protection-atp"></a>Advanced Threat Protection в Защитнике Windows (ATP)

Датчики глубокого анализа и ответные действия платформы ATP выявляют атаки на уровне памяти и ядра и реагируют на них путем подавления вредоносных файлов и завершения вредоносных процессов.

-   Подробные сведения об ATP в Защитнике Windows см. в статье [Overview of Microsoft Defender ATP capabilities](/windows/security/threat-protection/windows-defender-atp/overview) (Обзор возможностей ATP в Защитнике Windows).

-   Подробные сведения о подключении серверов см. в статье [Onboard servers to the Microsoft Defender ATP service](/windows/security/threat-protection/windows-defender-atp/configure-server-endpoints-windows-defender-advanced-threat-protection) (Подключение серверов к службе ATP в Защитнике Windows).

**Exploit Guard для ATP в Защитнике Windows** представляет собой новый набор средств предотвращения вторжений в узлы. Четыре компонента Exploit Guard в Защитнике Windows предназначены для блокировки различных векторов атак на устройство, а также блокировки поведений, которые часто используются в атаках с использованием вредоносных программ, при одновременном сохранении баланса между активным реагированием на угрозы безопасности и производительностью.

-   [Сокращение направлений атак (ASR)](/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard?ocid=cx-blog-mmpc) — это набор элементов управления, которые предприятия могут использовать для предотвращения попадания вредоносных программ на компьютер путем блокировки подозрительных вредоносных файлов (например, файлов Office), скриптов, бокового смещения, программ-шантажистов и угроз на основе электронной почты.

-   Функция [Защита сети](/windows/security/threat-protection/microsoft-defender-atp/network-protection) защищает конечные точки от веб-угроз, блокируя любые процессы на устройстве, идущие к недоверенным узлам и IP-адресам, с помощью фильтра SmartScreen Защитника Windows.

-   Функция [Контролируемый доступ к файлам](https://cloudblogs.microsoft.com/microsoftsecure/2017/10/23/stopping-ransomware-where-it-counts-protecting-your-data-with-controlled-folder-access/?ocid=cx-blog-mmpc?source=mmpc) защищает конфиденциальные данные от программ-шантажистов, блокируя доступ недоверенных процессов к защищенным папкам.

-   [Защита от эксплойтов](/windows/security/threat-protection/windows-defender-exploit-guard/exploit-protection-exploit-guard) — это набор мер защиты от уязвимостей (замена EMET), которые можно легко настроить для обеспечения безопасности системы и приложений.

Функция [Управление приложениями в Защитнике Windows](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) (также известна как политика целостности кода (CI) была представлена в Windows Server 2016.
Пользователи сообщали, что это отличное решение, которое, однако, сложно развернуть.
Для решения этой проблемы мы создали политики целостности кода по умолчанию, которые разрешают исполнение всех файлов, по умолчанию входящих в состав Windows, и приложений Microsoft (например, SQL Server) и блокируют исполнение известных исполняемых файлов, способных обойти политику целостности кода. 

### <a name="security-with-software-defined-networking-sdn"></a>Безопасность программно-конфигурируемых сетей (SDN)

Функция [Безопасность для SDN](../networking/sdn/security/sdn-security-top.md) предоставляет множество возможностей для безопасного выполнения рабочих нагрузок клиентами как в локальной среде, так и в качестве поставщика услуг в облаке. 

Эти усовершенствования безопасности интегрированы в многофункциональную платформу SDN, появившуюся в Windows Server 2016.

Полный список новых возможностей SDN доступен в статье [Что нового в программно-конфигурируемой сети (SDN) для Windows Server 2019?](../networking/sdn/sdn-whats-new.md)

### <a name="shielded-virtual-machines-improvements"></a>Улучшения экранированных виртуальных машин

- **Улучшения для филиалов**

    Теперь экранированные виртуальные машины можно запускать на компьютерах с периодическими разрывами подключения к службе защиты узла, используя новый [резервный сервер HGS](../security/guarded-fabric-shielded-vm/guarded-fabric-manage-branch-office.md#fallback-configuration) и [автономный режим](../security/guarded-fabric-shielded-vm/guarded-fabric-manage-branch-office.md#offline-mode). Резервный сервер HGS позволяет настроить второй набор URL-адресов для Hyper-V, который будет использоваться в случае невозможности установить подключение к основному серверу HGS.

    Автономный режим дает возможность продолжить запуск экранированных виртуальных машин, даже если не удается установить подключение к HGS при условии, что виртуальная машина была успешно запущена хотя бы один раз и в конфигурацию системы безопасности узла не вносились изменения.

- **Дополнительные возможности устранения неполадок**

    Мы также упростили процесс [устранения неполадок в работе экранированных виртуальных машин](../security/guarded-fabric-shielded-vm/guarded-fabric-troubleshoot-shielded-vms.md) за счет добавления поддержки режима расширенного сеанса VMConnect и PowerShell Direct. Эти средства будут особенно полезны при потере сетевого подключения к виртуальной машине и возникновении необходимости обновить ее конфигурацию, чтобы восстановить доступ. 

    Эти функции не нужно настраивать, они становятся доступны автоматически, когда экранированная виртуальная машина размещается на узле Hyper-V под управлением Windows Server версии 1803 или выше.

- **Поддержка Linux**

    Теперь Windows Server 2019 поддерживает выполнение систем Ubuntu, Red Hat Enterprise Linux и SUSE Linux Enterprise Server внутри экранированных виртуальных машина при работе в средах со смешанными ОС.

### <a name="http2-for-a-faster-and-safer-web"></a>HTTP/2 для более быстрого и безопасного просмотра веб-страниц

- Улучшенное объединение подключений исключает сбои при работе в Интернете, а также обеспечивает правильное шифрование веб-сеансов.

- Обновленный процесс согласования наборов шифров на стороне сервера в HTTP/2 обеспечивает автоматическое устранение сбоев подключений и удобство развертывания.

- Мы сделали CUBIC поставщиком контроля перегрузки протокола TCP по умолчанию, чтобы еще больше повысить пропускную способность!

## <a name="storage"></a>Хранение

Вот некоторые изменения, которые мы внесли в хранилище в Windows Server 2019. Подробные сведения см. в статье [What's new in Storage in Windows Server](../storage/whats-new-in-storage.md) (Новые возможности хранилища в Windows Server).

### <a name="storage-migration-service"></a>Служба миграции хранилища

Служба миграции хранилища — это новая технология, которая упрощает перенос серверов в более новую версию Windows Server. Она предоставляет графическое средство, которое выполняет инвентаризацию данных на серверах, передает данные и конфигурации на новые серверы, а затем при необходимости перемещает удостоверения старых серверов на новые серверы, чтобы пользователям и приложениям не требовалось вносить какие-либо изменения. Подробные сведения см. в разделе [Storage Migration Service overview](../storage/storage-migration-service/overview.md) (Обзор службы миграции хранилища).

### <a name="storage-spaces-direct"></a>Дисковые пространства прямого подключения

Ниже приведен список новых возможностей в Локальных дисковых пространствах. Подробные сведения см. в разделе [Storage Spaces Direct (Windows Server 2019 only)](../storage/whats-new-in-storage.md#storage-spaces-direct) (Локальные дисковые пространства (только для Windows Server 2019). Информацию о приобретении проверенных систем с Локальными дисковыми пространствами см. в статье [Общие сведения об Azure Stack HCI](/azure-stack/operator/azure-stack-hci-overview).

- **Дедупликация и сжатие томов ReFS**
- **Встроенная поддержка энергонезависимой памяти**
- **Вложенная устойчивость гиперконвергентной инфраструктуры с двумя узлами на границе**
- **Кластеры из двух серверов, использующие USB-устройство флэш-памяти в качестве свидетеля**
- **Поддержка Windows Admin Center**
- **Журнал производительности**
- **Масштабирование до 4 ПБ на кластер**
- **Контроль четности с зеркальным ускорением вдвое быстрее**
- **Обнаружение выброса задержки диска**
- **Разграничение выделения томов вручную для повышения отказоустойчивости**

### <a name="storage-replica"></a>Реплика хранилища

Новые возможности в реплике хранилища. Подробные сведения см. в разделе [Storage Replica](../storage/whats-new-in-storage.md#storage-replica) (Реплика хранилища).

- Реплика хранилища теперь доступна в Windows Server 2019 Standard Edition.
- Тестовая отработка отказа — это новая функция, которая позволяет подключать целевое хранилище для проверки репликации или резервного копирования данных. Подробные сведения см. в статье [с часто задаваемыми вопросами о реплике хранилища](../storage/storage-replica/storage-replica-frequently-asked-questions.md).
- Улучшения производительности журнала реплики хранилища
- Поддержка Windows Admin Center

## <a name="failover-clustering"></a>Отказоустойчивая кластеризация

Ниже приведен список новых возможностей отказоустойчивой кластеризации. Подробные сведения см. в статье [What's new in Failover Clustering](../failover-clustering/whats-new-in-failover-clustering.md) (Новые возможности отказоустойчивой кластеризации).

- **Наборы кластеров**
- **Кластеры с поддержкой Azure**
- **Миграция кластеров между доменами**
- **Свидетель USB**
- **Улучшения инфраструктуры кластера**
- **Кластерное обновление поддерживает локальные дисковые пространства**
- **Улучшения файлового ресурса-свидетеля**
- **Усиление защиты кластера**
- **Отказоустойчивый кластер больше не использует аутентификацию NTLM**

## <a name="application-platform"></a>Платформы приложений

### <a name="linux-containers-on-windows"></a>Контейнеры Linux в Windows

Теперь можно запускать контейнеры на основе Windows и Linux на одном и том же узле контейнера с помощью одной управляющей программы Docker. Это позволяет работать в разнородной среде узлов контейнеров и повысить гибкость разработчиков при создании приложений.

### <a name="built-in-support-for-kubernetes"></a>Реализация поддержки Kubernetes

В Windows Server 2019 улучшены функции вычислений, сети и хранилища выпусков Semi-Annual Channel, необходимых для реализации поддержки платформы Kubernetes в Windows. Дополнительная информация будет доступна в следующих выпусках Kubernetes.

- [Средства работы с сетевыми подключениями контейнеров](../networking/sdn/technologies/containers/container-networking-overview.md) в Windows Server 2019 значительно повышают удобство использования Kubernetes в Windows за счет улучшения устойчивости сети платформы и поддержки подключаемых модулей сетевых подключений контейнеров.

- Развернутые в Kubernetes рабочие нагрузки могут использовать средства сетевой безопасности для защиты служб Linux и Windows с помощью встроенных механизмов безопасности.

### <a name="container-improvements"></a>Улучшения контейнеров
    
- **Улучшенные интегрированные удостоверения**

    Мы упростили процесс встроенной проверки подлинности Windows в контейнерах и повысили ее надежность, устранив некоторые ограничения предыдущих выпусков Windows Server.

- **Улучшенная совместимость приложений**

    Упрощено создание контейнеров приложений Windows: улучшена совместимость приложений для имеющегося образа *windowsservercore*. Приложениям с дополнительными зависимостями API теперь доступен третий базовый образ, *windows*.

- **Уменьшение размера и повышение производительности**

    Были уменьшены размеры файлов для скачивания базовых образов контейнеров и необходимое пространство на диске, а также ускорено время запуска. Это ускоряет рабочие процессы контейнеров.

- **Интерфейс администрирования в Windows Admin Center \((предварительная версия)\)**

    Мы значительно упростили мониторинг контейнеров, запущенных на вашем компьютере, а также управление отдельными контейнерами с помощью нового расширения для Windows Admin Center. Найдите расширение "Контейнеры" в [общедоступном веб-канале Windows Admin Center](../manage/windows-admin-center/configure/using-extensions.md).

### <a name="encrypted-networks"></a>Зашифрованные сети

[Зашифрованные сети](../networking/sdn/sdn-whats-new.md) — функция шифрования виртуальных сетей, позволяющая шифровать трафик виртуальной сети между виртуальными машинами, которые обмениваются данными между собой в подсетях с пометкой **Включено шифрование**. Для шифрования пакетов с помощью этой возможности также используется протокол DTLS в виртуальной подсети. Протокол DTLS обеспечивает защиту от перехвата, несанкционированных изменений и подделки со стороны любых лиц, имеющих доступ к физической сети.

### <a name="network-performance-improvements-for-virtual-workloads"></a>Повышение производительности сети для виртуальных рабочих нагрузок

[Повышение производительности сети для виртуальных рабочих нагрузок](../networking/technologies/hpn/hpn-insider-preview.md) обеспечивает максимальную пропускную способность сети для виртуальных машин без необходимости постоянной настройки или избыточного предоставления ресурсов узла. За счет этого сокращаются расходы на эксплуатацию и обслуживание и одновременно повышается доступная плотность узлов. Новые функции:

* объединение полученных сегментов в виртуальном коммутаторе;

* динамическое управление несколькими очередями виртуальных машин (d.VMMQ).

### <a name="low-extra-delay-background-transport"></a>Передача данных с помощью алгоритма Low Extra Delay Background Transport

Low Extra Delay Background Transport (LEDBAT) — это поставщик управления перегрузкой сети с низкой задержкой, разработанный для автоматического повышения пропускной способности для пользователей и приложений и потребления всей доступной пропускной способности, когда сеть не используется.   
Эта технология предназначена для применения при развертывании крупных критических обновлений в ИТ-среде без ущерба для служб, использующихся пользователями, и связанной с ними пропускной способности.

### <a name="windows-time-service"></a>служба времени Windows

В [службе времени Windows](../networking/windows-time-service/insider-preview.md) реализована полноценная поддержка UTC-совместимой корректировочной секунды, новый протокол времени под названием "Протокол точного времени" (Precision Time Protocol), а также трассировка в сквозном режиме.


### <a name="high-performance-sdn-gateways"></a>Высокопроизводительные шлюзы SDN

[Высокопроизводительные шлюзы SDN](../networking/sdn/gateway-performance.md) в Windows Server 2019 значительно повышают производительность подключений IPsec и GRE, обеспечивая сверхвысокую пропускную способность при гораздо меньшей нагрузке на ЦП.
<br/>

### <a name="new-deployment-ui-and-windows-admin-center-extension-for-sdn"></a>Новый пользовательский интерфейс развертывания и расширение Windows Admin Center для SDN

Теперь в Windows Server 2019 можно легко выполнять развертывание и управление с помощью нового пользовательского интерфейса для развертывания, а также расширения Windows Admin Center, которое предоставляет возможности SDN всем пользователям. 

### <a name="persistent-memory-support-for-hyper-v-vms"></a>Поддержка энергонезависимой памяти для виртуальных машин Hyper-V

Обеспечение высокой пропускной способности и низкой задержки энергозависимой памяти (или памяти хранилища) для виртуальных машин за счет прямой реализации этой функции в виртуальных машинах. Это позволяет существенно уменьшить задержку транзакций базы данных и сократить время восстановления баз данных с низкой задержкой в памяти в случае сбоя.
