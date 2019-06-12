---
title: Диагностика стека программно-конфигурируемой сети Windows Server
description: В этом руководстве Windows Server проверяет распространенных ошибок программно определяемой сети (SDN) и сценарии сбоев и описываются устранения неполадок рабочего процесса, который использует доступные средства диагностики.
manager: ravirao
ms.prod: windows-server-threshold
ms.technology: networking-sdn
ms.topic: article
ms.assetid: 9be83ed2-9e62-49e8-88e7-f52d3449aac5
ms.author: pashort
author: JMesser81
ms.date: 08/14/2018
ms.openlocfilehash: eeb0c335e4afd3c6835a04421a15073aeab6cdc6
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66446239"
---
# <a name="troubleshoot-the-windows-server-software-defined-networking-stack"></a>Диагностика стека программно-конфигурируемой сети Windows Server

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

В этом руководстве рассматриваются распространенные ошибки программно определяемой сети (SDN) и сценарии сбоев и описываются устранения неполадок рабочего процесса, который использует доступные средства диагностики.  

Дополнительные сведения о корпорации Майкрософт программно-Конфигурируемую сеть, см. в разделе [программно-Конфигурируемую сеть](../../sdn/Software-Defined-Networking--SDN-.md).  

## <a name="error-types"></a>Типы ошибок  
В следующем списке представляет класс проблем, которые чаще всего встречается с виртуализацией сети Hyper-V (HNVv1) в Windows Server 2012 R2, от развертывания в рабочей среде на рынок и точка во многом совпадает с теми же типами проблемы в Windows Server 2016 HNVv2 с новый стек программно определяемой сети (SDN).  

Большинство ошибок можно разделить на небольшой набор классов:   
* **Недопустимый или неподдерживаемый конфигурации**  
   Пользователь вызывает Северный API-Интерфейс, неправильно или с недопустимыми политиками.   

* **Ошибка в приложении политики**  
     Политики из сетевого контроллера не было доставлено на узел Hyper-V, значительно отложенной и / или не обновлена на всех узлах Hyper-V (например, после динамической миграции).  
* **Ошибка конфигурации смещение или программного обеспечения**  
  Путь к данным проблемы, возникшие в пакетах.  

* **Внешних ошибках, связанных с сетевой Адаптер оборудования и драйверов или лежащие сетевой структуры**  
  Неправильно вести себя Разгрузка задач (например, VMQ) или лежащие структуры сети настроен неправильно (например, MTU)   

  Это руководство по устранению неполадок проверяет каждую из этих категорий ошибок и рекомендует рекомендации и средства диагностики, доступные для выявления и исправления ошибки.  

## <a name="diagnostic-tools"></a>Средства диагностики  

Прежде чем обсуждать по устранению неполадок рабочих процессов для каждого из подобных ошибок, давайте рассмотрим доступные средства диагностики.   

Чтобы использовать средства диагностики сетевого контроллера (элемент управления path), необходимо сначала установить компонент RSAT NetworkController и импортировать ``NetworkControllerDiagnostics`` модуля:  

```  
Add-WindowsFeature RSAT-NetworkController -IncludeManagementTools  
Import-Module NetworkControllerDiagnostics  
```  

Чтобы использовать средства диагностики HNV диагностики (data-path), необходимо импортировать ``HNVDiagnostics`` модуля:

```  
# Assumes RSAT-NetworkController feature has already been installed
Import-Module hnvdiagnostics   
```  

### <a name="network-controller-diagnostics"></a>Диагностика сети контроллера  
Эти командлеты документированы в библиотеке TechNet в [раздела командлета диагностики сетевого контроллера](https://docs.microsoft.com/powershell/module/networkcontrollerdiagnostics/). Они помогают выявить проблемы с согласованностью политики сети в элемент управления пути между узлами сетевого контроллера, а также между сетевого контроллера и агентов узла сетевого Контроллера, работающих на узлах Hyper-V.

 _Отладки ServiceFabricNodeStatus_ и _Get NetworkControllerReplica_ командлеты необходимо запускать из одной из виртуальных машин узла сетевого контроллера. Все командлеты NC диагностики можно запустить из любой узел, который может подключиться к сетевым контроллером и выполняется либо в группу управления сетевым контроллером (Kerberos) или имеет доступ к сертификату X.509 для управления сетевым контроллером. 

### <a name="hyper-v-host-diagnostics"></a>Диагностика узла Hyper-V  
Эти командлеты документированы в библиотеке TechNet в [раздела командлета диагностики виртуализации сети Hyper-V (HNV)](https://docs.microsoft.com/powershell/module/hnvdiagnostics/). Они помогают выявить проблемы в обмена данными между виртуальными машинами клиентов (Восток/запад) и входящего трафика через SLB, виртуальный IP-адрес (/ вниз). 

_Отладки VirtualMachineQueueOperation_, _Get-CustomerRoute_, _Get-PACAMapping_, _Get-ProviderAddress_, _Get-VMNetworkAdapterPortId_, _Get-VMSwitchExternalPortId_, и _EncapOverheadSettings теста_ являются все локальные тесты, которые могут быть вызваны из любого узла Hyper-V. Другие командлеты вызывать тесты путь к данным через сетевой контроллер и поэтому нужен доступ к сетевому контроллеру как descried выше.

### <a name="github"></a>GitHub
[Репозиторий GitHub Microsoft/SDN](https://github.com/microsoft/sdn) имеет ряд примеров сценариев и рабочие процессы, которые основаны на этих командлетов в поле. В частности, сценарии диагностики можно найти в [диагностики](https://github.com/Microsoft/sdn/diagnostics) папки. Помогите нам способствующих эти сценарии, отправляя запросы на включение внесенных изменений.

## <a name="troubleshooting-workflows-and-guides"></a>Устранение неполадок рабочих процессов и руководства  

### <a name="hoster-validate-system-health"></a>[Поставщика услуг размещения] Проверки работоспособности системы
Отсутствует внедренный ресурс с именем _состояние конфигурации_ в несколько ресурсов сетевого контроллера. Состояние конфигурации сведения о работоспособности системы, включая согласованность конфигурации сетевого контроллера и фактическое состояние (выполнения) на узлах Hyper-V. 

Чтобы проверить состояние конфигурации, выполните следующую команду из любой узел Hyper-V с подключением к сетевому контроллеру.

>[!NOTE] 
>Значение для *NetworkController* параметра должно быть полное доменное имя или IP-адрес, основанный на имени субъекта X.509 > сертификат, созданный для сетевого контроллера.
>
>*Учетных данных* только необходимо указать параметр, если сетевой контроллер с помощью проверки подлинности Kerberos (обычно в развертываниях VMM). Учетные данные должны предназначаться для пользователя, который входит в группу безопасности сети контроллера управления.

```none
Debug-NetworkControllerConfigurationState -NetworkController <FQDN or NC IP> [-Credential <PS Credential>]

# Healthy State Example - no status reported
$cred = Get-Credential
Debug-NetworkControllerConfigurationState -NetworkController 10.127.132.211 -Credential $cred

Fetching ResourceType:     accessControlLists
Fetching ResourceType:     servers
Fetching ResourceType:     virtualNetworks
Fetching ResourceType:     networkInterfaces
Fetching ResourceType:     virtualGateways
Fetching ResourceType:     loadbalancerMuxes
Fetching ResourceType:     Gateways
```

Ниже приведен пример сообщения состояния конфигурации:

```none
Fetching ResourceType:     servers
---------------------------------------------------------------------------------------------------------
ResourcePath:     https://10.127.132.211/Networking/v1/servers/4c4c4544-0056-4b10-8058-b8c04f395931
Status:           Warning

Source:           SoftwareLoadBalancerManager
Code:             HostNotConnectedToController
Message:          Host is not Connected.
----------------------------------------------------------------------------------------------------------
```

>[!NOTE]
> Это ошибка в системе, где ресурсы сетевого интерфейса для сетевой КАРТЫ виртуальной Машины SLB/Mux передаче находятся в состоянии сбоя с ошибкой «Виртуального коммутатора — узла не подключен к Controller». Можно спокойно проигнорировать эту ошибку, если IP-конфигурации в ресурсе сетевого Адаптера виртуальной Машины IP-адрес из пула IP-адресов транзитной логической сети. Это вторая ошибка в системе, где ресурсы сетевого интерфейса для сетевых адаптеров виртуальной Машины поставщика HNV шлюза находятся в состоянии сбоя с ошибкой «PortBlocked — виртуальный коммутатор». Эту ошибку можно также проигнорировать Если IP-конфигурации в ресурсе сетевого Адаптера виртуальной Машины задано значение null (так предусмотрено разработчиками).


В следующей таблице перечислены коды ошибок, сообщения и дальнейшие действия будут выполняться для наблюдаемых состояние конфигурации.


| **Код**| **Сообщение**| **Действие**|  
|--------|-----------|----------|  
| Неизвестно| Неизвестная ошибка| |  
| HostUnreachable                       | Хост-компьютер недоступен | Проверьте сетевое подключение управления между сетевого контроллера и узлов |  
| PAIpAddressExhausted                  | PA IP-адреса, исчерпаны | Увеличьте размер пула IP-адрес для логической подсети поставщика HNV |  
| PAMacAddressExhausted                 | PA Mac-адреса исчерпаны | Увеличить диапазон пула Mac-адресов |  
| PAAddressConfigurationFailure         | Не удалось выполнить для настройки сетевого адреса типа АП на узел | Проверьте сетевое подключение управления между сетевым контроллером и узлом. |  
| CertificateNotTrusted                 | Сертификат не является доверенным  |Исправьте сертификатов, используемых для связи с узлом. |  
| CertificateNotAuthorized              | Сертификат не авторизован | Исправьте сертификатов, используемых для связи с узлом. |  
| PolicyConfigurationFailureOnVfp       | Сбой при настройке политики VFP | Это происходит сбой выполнения.  Нет определенного способы. Сбор журналов. |  
| PolicyConfigurationFailure            | Сбой в Отправка политики в узлах, из-за сбоя соединения или другие ошибки в NetworkController.| Нет определенного действия.  Это из-за сбоя в целевое состояние обработки в модулях сетевого контроллера. Сбор журналов. |  
| HostNotConnectedToController          | Узел еще не подключен к сетевым контроллером | Профиль порта, не применяется на узел или узел недостижим из сетевого контроллера. Проверить, что раздел реестра HostID совпадает с Идентификатором экземпляра ресурса сервера |  
| MultipleVfpEnabledSwitches            | Существует несколько VFp включена коммутаторов на узле  | Удалите один из параметров, так как агент узла сетевого контроллера поддерживает только один виртуальный коммутатор с включенным расширением VFP |  
| PolicyConfigurationFailure            | Не удалось принудительно отправить политики виртуальной сети для VmNic, из-за ошибки сертификата или ошибки подключения  | Проверьте, если соответствующие сертификаты были развернуты (имя субъекта сертификата должно соответствовать полное ДОМЕННОЕ имя узла). Также проверьте подключение к узлу с помощью сетевого контроллера |  
| PolicyConfigurationFailure            | Не удалось принудительно отправить политики виртуальный коммутатор для VmNic, из-за ошибки сертификата или ошибки подключения  | Проверьте, если соответствующие сертификаты были развернуты (имя субъекта сертификата должно соответствовать полное ДОМЕННОЕ имя узла). Также проверьте подключение к узлу с помощью сетевого контроллера|
| PolicyConfigurationFailure            | Не удалось принудительно отправить политики брандмауэра для VmNic, из-за ошибки сертификата или ошибки подключения | Проверьте, если соответствующие сертификаты были развернуты (имя субъекта сертификата должно соответствовать полное ДОМЕННОЕ имя узла). Также проверьте подключение к узлу с помощью сетевого контроллера|
| DistributedRouterConfigurationFailure | Не удалось настроить параметры распределенного маршрутизатора на виртуальном сетевом адаптере узла                          | Ошибка стека TCP/IP. Может потребоваться очистка PA и узла аварийного восстановления виртуальных сетевых адаптеров на сервере, на котором возникла ошибка |
| DhcpAddressAllocationFailure          | Сбой выделения адресов DHCP для VMNic                                                    | Проверьте, если атрибут статический IP-адрес адрес настраивается на ресурса сетевого Адаптера |  
| CertificateNotTrusted<br>CertificateNotAuthorized | Не удалось подключиться к мультиплексора из-за ошибок сети или cert | Проверьте числовой код, указанный в сообщении код ошибки: это соответствующий код ошибки winsock. Ошибки сертификата являются детализированными (например, не удается проверить сертификат, не авторизован cert и т. д.) |  
| HostUnreachable                       | Мультиплексора неработоспособна (распространенный случай — BGPRouter отключен) | Узел BGP RRAS (BGP виртуальная машина) или коммутатор верхнего (ToR) недоступен или не пиринга успешно. Проверьте параметры BGP на мультиплексора балансировщика нагрузки программного обеспечения ресурсов и узла BGP (ToR или RRAS виртуальная машина) |  
| HostNotConnectedToController          | Агент узла SLB не подключен  | Убедитесь, что запущена служба агента узла SLB; См. журналы агента узла SLB (автоматически под управлением) по причинам, в случае, если сертификат, представленный агент узла под управлением отклонено SLBM (NC) состояние покажет высококачественную информацию  |  
| PortBlocked                           | Порт VFP блокируется из-за отсутствия виртуальной сети и политики ACL | Проверьте наличие других ошибок, которые могут вызвать политики не задается. |  
| Перегрузка                            | Перегружен Мультиплексора балансировщика нагрузки  | Проблемы с производительностью с помощью Мультиплексора |  
| RoutePublicationFailure               | Маршрутизатор BGP не подключен Мультиплексора балансировщика нагрузки | Проверка, доступен ли Мультиплексор имеет соединение с маршрутизаторами BGP и пиринга BGP настроено правильно |  
| VirtualServerUnreachable              | Мультиплексора балансировщика нагрузки не подключен к диспетчера SLB | Проверьте подключение между SLBM и Мультиплексора |  
| QosConfigurationFailure               | Не удалось настроить политики качества Обслуживания | См. в разделе, если имеет достаточную пропускную способность для всех виртуальных Машин при использовании резервирования QOS |


#### <a name="check-network-connectivity-between-the-network-controller-and-hyper-v-host-nc-host-agent-service"></a>Проверьте сетевое подключение между сетевым контроллером и узлом Hyper-V (служба агента узла сетевого Контроллера)
Запустите *netstat* следующую команду, чтобы проверить, что существуют три УСТАНОВЛЕНО соединений между агент узла сетевого Контроллера и узлов сетевого контроллера и одного сокета ожидает ВЫЗОВА на узле Hyper-V
- ПРОСЛУШИВАЕТ порт TCP:6640 на узле Hyper-V (служба агента узла сетевого Контроллера)
- IP-адрес на порте 6640 IP-адрес узла сетевого Контроллера на временные порты (> 32000) узла два установленных подключений из Hyper-V
- Один установленное соединение из IP-адрес узла Hyper-V на временных портов IP-адрес REST контроллера сети через порт 6640

>[!NOTE]
>Может существовать только двух подключений, установленных на узле Hyper-V при наличии не клиента виртуальных машин, развернутых на этом конкретном узле.

```none
netstat -anp tcp |findstr 6640

# Successful output
  TCP    0.0.0.0:6640           0.0.0.0:0              LISTENING
  TCP    10.127.132.153:6640    10.127.132.213:50095   ESTABLISHED
  TCP    10.127.132.153:6640    10.127.132.214:62514   ESTABLISHED
  TCP    10.127.132.153:50023   10.127.132.211:6640    ESTABLISHED
```
#### <a name="check-host-agent-services"></a>Проверка службы агента узла
Сетевой контроллер взаимодействует с двумя службами агента узла на узлах Hyper-V: Агент узла SLB и агент узла сетевого Контроллера. Вполне возможно, что одно или оба этих служб не запущена. Проверьте их состояние и перезапустить, если они не были запущены.

```none
Get-Service SlbHostAgent
Get-Service NcHostAgent

# (Re)start requires -Force flag
Start-Service NcHostAgent -Force
Start-Service SlbHostAgent -Force
```

#### <a name="check-health-of-network-controller"></a>Проверьте работоспособность сетевого контроллера
Если не три соединения УСТАНОВЛЕНО или сетевой контроллер не отвечает, проверьте, что все узлы и модули службы, приступить к работе с помощью следующих командлетов. 

```none
# Prints a DIFF state (status is automatically updated if state is changed) of a particular service module replica 
Debug-ServiceFabricNodeStatus [-ServiceTypeName] <Service Module>
```
В модулях службы сетевого контроллера можно:
- ControllerService
- ApiService
- SlbManagerService
- ServiceInsertion
- FirewallService
- VSwitchService
- GatewayManager
- FnmService
- HelperService
- UpdateService

Убедитесь, что состояние ReplicaStatus находится **готовы** и HealthState **ОК**.

В рабочей среде развертывания — с несколькими узлами сетевого контроллера, вы также можете проверить, каждая служба является первичной для узла и его состояние отдельной реплики.

```none  
Get-NetworkControllerReplica

# Sample Output for the API service module 
Replicas for service: ApiService

ReplicaRole   : Primary
NodeName      : SA18N30NC3.sa18.nttest.microsoft.com
ReplicaStatus : Ready

```
Убедитесь, что состояние реплики все готово для каждой службы.

#### <a name="check-for-corresponding-hostids-and-certificates-between-network-controller-and-each-hyper-v-host"></a>Проверка наличия соответствующей HostIDs и сертификаты между сетевым контроллером и каждом узле Hyper-V 
На узле Hyper-V выполните следующие команды, чтобы проверить, что HostID соответствует идентификатору экземпляра ресурса сервера в сетевом контроллере.

```none
Get-ItemProperty "hklm:\system\currentcontrolset\services\nchostagent\parameters" -Name HostId |fl HostId

HostId : **162cd2c8-08d4-4298-8cb4-10c2977e3cfe**

Get-NetworkControllerServer -ConnectionUri $uri |where { $_.InstanceId -eq "162cd2c8-08d4-4298-8cb4-10c2977e3cfe"}

Tags             :
ResourceRef      : /servers/4c4c4544-0056-4a10-8059-b8c04f395931
InstanceId       : **162cd2c8-08d4-4298-8cb4-10c2977e3cfe**
Etag             : W/"50f89b08-215c-495d-8505-0776baab9cb3"
ResourceMetadata : Microsoft.Windows.NetworkController.ResourceMetadata
ResourceId       : 4c4c4544-0056-4a10-8059-b8c04f395931
Properties       : Microsoft.Windows.NetworkController.ServerProperties
```

*Исправление* Если с помощью SDNExpress сценариев или развертывание вручную обновить HostId ключ в реестре в соответствии с идентификатором экземпляра ресурсов сервера. Перезапустите агент узла сетевого контроллера на узле Hyper-V (репликация физических серверов), если с помощью VMM, удалите сервер Hyper-V из VMM и удалите раздел реестра HostId. Затем повторно добавьте на сервере с помощью VMM.


Проверьте, что отпечатки сертификатов X.509, используемый узлом Hyper-V (имя узла будет имя субъекта сертификата) для обмена данными (SouthBound) между узлом Hyper-V (служба агента узла сетевого Контроллера) и узлы сетевого контроллера совпадают. Также проверьте наличие имени субъекта сертификата REST сетевой контроллер *CN =<FQDN or IP>* .

```  
# On Hyper-V Host
dir cert:\\localmachine\my  

Thumbprint                                Subject
----------                                -------
2A3A674D07D8D7AE11EBDAC25B86441D68D774F9  CN=SA18n30-4.sa18.nttest.microsoft.com
...

dir cert:\\localmachine\root

Thumbprint                                Subject
----------                                -------
30674C020268AA4E40FD6817BA6966531FB9ADA4  CN=10.127.132.211 **# NC REST IP ADDRESS**

# On Network Controller Node VM
dir cert:\\localmachine\root  

Thumbprint                                Subject
----------                                -------
2A3A674D07D8D7AE11EBDAC25B86441D68D774F9  CN=SA18n30-4.sa18.nttest.microsoft.com
30674C020268AA4E40FD6817BA6966531FB9ADA4  CN=10.127.132.211 **# NC REST IP ADDRESS**
...
```  

Вы также можете проверить параметры каждого сертификата, чтобы убедиться, что имя субъекта является то, что такое ожидается (имя узла или полное доменное имя NC REST или IP-адрес), сертификат еще не истек, и все центры сертификации в цепи сертификатов включаются в доверенном корневом каталоге Центр сертификации.

- Имя субъекта  
- Дата окончания срока действия  
- Доверенным корневым центром сертификации  

*Исправление* Если несколько сертификатов имеет то же имя субъекта на узле Hyper-V, агент узла сетевого контроллера случайным образом выбирает одну для сетевого контроллера. Это может не соответствовать отпечаток ресурс сервера, известный сетевого контроллера. В этом случае удалите один из сертификатов с тем же именем субъекта, на узле Hyper-V и затем повторно запустите ее агент узла сетевого контроллера. Если, можно по-прежнему не удается установить соединение, удалите другой сертификат с тем же именем субъекта, на узле Hyper-V и соответствующий ресурс сервера в VMM. Затем повторно создайте ресурс сервера в VMM, который создаст новый сертификат X.509 и установить его на узле Hyper-V.


#### <a name="check-the-slb-configuration-state"></a>Проверьте состояние конфигурации SLB
Состояние конфигурации SLB может определяться как часть выходные данные командлету Debug-NetworkController. Этот командлет также будет выводить текущего набора ресурсы сетевого контроллера в JSON-файлы, все IP-конфигурации из каждого узла Hyper-V (сервер) и локальная политика сети из таблиц базы данных агента узла. 

По умолчанию будут собираться дополнительные трассировки. Чтобы не собирать трассировки, добавьте - IncludeTraces: параметр $false.

```none
Debug-NetworkController -NetworkController <FQDN or IP> [-Credential <PS Credential>] [-IncludeTraces:$false]

# Don't collect traces
$cred = Get-Credential 
Debug-NetworkController -NetworkController 10.127.132.211 -Credential $cred -IncludeTraces:$false

Transcript started, output file is C:\\NCDiagnostics.log
Collecting Diagnostics data from NC Nodes
```

>[!NOTE]
>Расположение выходных данных по умолчанию будет находиться в каталоге \NCDiagnostics\ < working_directory >. Выходной каталог по умолчанию можно изменить с помощью `-OutputDirectory` параметра. 

Сведения о состоянии конфигурации SLB можно найти в _slbstateResults.Json диагностики_ файл в этом каталоге.

Этот JSON-файл можно разделить на следующие разделы:
 * Структура
   * SlbmVips - в этом разделе перечислены IP-адрес диспетчера SLB виртуальный IP-адрес, используемый сетевым контроллером для coodinate конфигурации и работоспособности Мультиплексорами SLB и SLB узлов агентов.
   * MuxState - в этом разделе будут отображаться одно значение для каждого SLB/Mux развернутых предоставляя состояние мультиплексора.
   * Настройка маршрутизатора — в этом разделе будут перечислены вышестоящего маршрутизатора (узла BGP) номера автономных систем (ASN), время передачи IP-адрес и идентификатор. Также будут перечислены ASN Мультиплексорами SLB и передаче IP-адрес.
   * Подключенные сведений об узле — в этом разделе будет список IP-адрес управления адрес всех узлов Hyper-V, доступных для запуска рабочих нагрузок с балансировкой нагрузки.
   * Диапазоны виртуальных IP-адресов — в этом разделе будут перечислены диапазоны пула общедоступных и частных виртуальных IP-адресов IP-адресов. SLBM VIP, будут включены как выделенный IP-адрес из одного из этих диапазонов. 
   * Маршруты мультиплексора - в этом разделе будут отображаться одно значение для каждого SLB/Mux развертывания содержит все объявления маршрутов для этого конкретного мультиплексора.
 * Клиент
   * VipConsolidatedState - в этом разделе будут отображаться подключения его состояние каждого VIP-адреса клиента, включая префикс объявленных маршрутов, узел Hyper-V и конечные точки DIP.

> [!NOTE]
> Возможно установить состояние SLB напрямую с помощью [DumpSlbRestState](https://github.com/Microsoft/SDN/blob/master/Diagnostics/DumpSlbRestState.ps1) скрипт, доступный на [репозитория Microsoft SDN GitHub](https://github.com/microsoft/sdn). 

#### <a name="gateway-validation"></a>Проверка шлюза

**Из сетевого контроллера:**
```
Get-NetworkControllerLogicalNetwork
Get-NetworkControllerPublicIPAddress
Get-NetworkControllerGatewayPool
Get-NetworkControllerGateway
Get-NetworkControllerVirtualGateway
Get-NetworkControllerNetworkInterface
```

**Из шлюза виртуальной Машины:**
```
Ipconfig /allcompartments /all
Get-NetRoute -IncludeAllCompartments -AddressFamily
Get-NetBgpRouter
Get-NetBgpRouter | Get-BgpPeer
Get-NetBgpRouter | Get-BgpRouteInformation
```

**Сверху стоечного коммутатора:**

`sh ip bgp summary (for 3rd party BGP Routers)`

**Маршрутизатор BGP Windows**
```
Get-BgpRouter
Get-BgpPeer
Get-BgpRouteInformation
```

Помимо этих проблем, который мы видели до сих (особенно на основе SDNExpress развертывания) наиболее распространенными причинами секции клиента, не начало настроен на виртуальных машинах GW казаться, что тот факт, что производительность GW в FabricConfig.psd1 — меньше по сравнению с что Специалисты по попытаемся назначить сетевые подключения (туннели S2S) в TenantConfig.psd1. Это можно легко проверить, сравнивая выходные данные из следующих команд:

```
PS > (Get-NetworkControllerGatewayPool -ConnectionUri $uri).properties.Capacity
PS > (Get-NetworkControllerVirtualgatewayNetworkConnection -ConnectionUri $uri -VirtualGatewayId "TenantName").properties.OutboundKiloBitsPerSecond
PS > (Get-NetworkControllerVirtualgatewayNetworkConnection -ConnectionUri $uri -VirtualGatewayId "TenantName").property
```

### <a name="hoster-validate-data-plane"></a>[Поставщика услуг размещения] Проверка плоскости данных
После развертывания сетевого контроллера и клиента виртуальные сети и подсети будут созданы виртуальные машины были вложены в виртуальных подсетях, поставщиком услуг размещения, чтобы проверить возможность подключения клиента можно выполнить проверку уровня дополнительной структуры.

#### <a name="check-hnv-provider-logical-network-connectivity"></a>Проверьте подключение к логической сети поставщика HNV
После первого гостевую виртуальную Машину на узле Hyper-V подключен к виртуальной сети клиента сетевой контроллер назначит два HNV поставщика IP-адреса (IP-адреса типа АП) на узле Hyper-V. Эти IP-адреса будут поступать из пула IP-адресов логической сети поставщика HNV и управляемых сетевым контроллером.  Чтобы узнать, каковы эти два IP-адреса HNV

```none
PS > Get-ProviderAddress

# Sample Output
ProviderAddress : 10.10.182.66
MAC Address     : 40-1D-D8-B7-1C-04
Subnet Mask     : 255.255.255.128
Default Gateway : 10.10.182.1
VLAN            : VLAN11

ProviderAddress : 10.10.182.67
MAC Address     : 40-1D-D8-B7-1C-05
Subnet Mask     : 255.255.255.128
Default Gateway : 10.10.182.1
VLAN            : VLAN11
```

Эти HNV поставщика IP-адреса (IP-адреса типа АП) назначаются адаптеры Ethernet, созданные в отдельной секции TCPIP сети и иметь имя адаптера _VLANX_ где X — виртуальной локальной сети, назначенные логической сети поставщика HNV (транспорт).

Связи между двумя узлами Hyper-V, с помощью поставщика HNV логической сети можно сделать, запрос проверки связи с дополнительные секции (-c Y) параметра, где Y — TCPIP секция сети, в котором были созданы PAhostVNICs. Этой секции можно определить, выполнив:

```none
C:\> ipconfig /allcompartments /all

<snip> ...
==============================================================================
Network Information for *Compartment 3*
==============================================================================
   Host Name . . . . . . . . . . . . : SA18n30-2
<snip> ...

Ethernet adapter VLAN11:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft Hyper-V Network Adapter
   Physical Address. . . . . . . . . : 40-1D-D8-B7-1C-04
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::5937:a365:d135:2899%39(Preferred)
   IPv4 Address. . . . . . . . . . . : 10.10.182.66(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.128
   Default Gateway . . . . . . . . . : 10.10.182.1
   NetBIOS over Tcpip. . . . . . . . : Disabled

Ethernet adapter VLAN11:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft Hyper-V Network Adapter
   Physical Address. . . . . . . . . : 40-1D-D8-B7-1C-05
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::28b3:1ab1:d9d9:19ec%44(Preferred)
   IPv4 Address. . . . . . . . . . . : 10.10.182.67(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.128
   Default Gateway . . . . . . . . . : 10.10.182.1
   NetBIOS over Tcpip. . . . . . . . : Disabled

*Ethernet adapter vEthernet (PAhostVNic):*
<snip> ...
```

>[!NOTE]
> Виртуальный сетевой адаптер PA адаптеров не используются в пути к данным, поэтому не IP-адрес «адаптера vEthernet (PAhostVNic)».

Например предположим, что узлы Hyper-V 1 и 2 имеют HNV поставщика (АП) IP-адреса:

|Узел hyper-V —|-IP-адрес PA 1|-IP-адрес PA 2|
|---             |---            |---             |
|Узел 1 | 10.10.182.64 | 10.10.182.65 |
|Узел 2 | 10.10.182.66 | 10.10.182.67 |

может проверить связь с между ними, используя следующую команду, чтобы проверить возможность подключения логической сети поставщика HNV.

```none
# Ping the first PA IP Address on Hyper-V Host 2 from the first PA IP address on Hyper-V Host 1 in compartment (-c) 3
C:\> ping -c 3 10.10.182.66 -S 10.10.182.64

# Ping the second PA IP Address on Hyper-V Host 2 from the first PA IP address on Hyper-V Host 1 in compartment (-c) 3
C:\> ping -c 3 10.10.182.67 -S 10.10.182.64

# Ping the first PA IP Address on Hyper-V Host 2 from the second PA IP address on Hyper-V Host 1 in compartment (-c) 3
C:\> ping -c 3 10.10.182.66 -S 10.10.182.65

# Ping the second PA IP Address on Hyper-V Host 2 from the second PA IP address on Hyper-V Host 1 in compartment (-c) 3
C:\> ping -c 3 10.10.182.67 -S 10.10.182.65
```

*Исправление* Если поставщика HNV ping не работает, проверьте подключение к физической сети, включая конфигурацию виртуальной ЛС. Физических сетевых адаптеров на каждом узле Hyper-V должен быть в режиме магистрали с определенной назначена виртуальная ЛС. Виртуальный сетевой адаптер узла управления должны быть изолированы для виртуальной ЛС логической сети управления.

```none
PS C:\> Get-NetAdapter "Ethernet 4" |fl

Name                       : Ethernet 4
InterfaceDescription       : <NIC> Ethernet Adapter
InterfaceIndex             : 2
MacAddress                 : F4-52-14-55-BC-21
MediaType                  : 802.3
PhysicalMediaType          : 802.3
InterfaceOperationalStatus : Up
AdminStatus                : Up
LinkSpeed(Gbps)            : 10
MediaConnectionState       : Connected
ConnectorPresent           : True
*VlanID                     : 0*
DriverInformation          : Driver Date 2016-08-28 Version 5.25.12665.0 NDIS 6.60

# VMM uses the older PowerShell cmdlet <Verb>-VMNetworkAdapterVlan to set VLAN isolation
PS C:\> Get-VMNetworkAdapterVlan -ManagementOS -VMNetworkAdapterName <Mgmt>

VMName VMNetworkAdapterName Mode     VlanList
------ -------------------- ----     --------
<snip> ...        
       Mgmt                 Access   7
<snip> ...

# SDNExpress deployments use the newer PowerShell cmdlet <Verb>-VMNetworkAdapterIsolation to set VLAN isolation
PS C:\> Get-VMNetworkAdapterIsolation -ManagementOS

<snip> ...

IsolationMode        : Vlan
AllowUntaggedTraffic : False
DefaultIsolationID   : 7
MultiTenantStack     : Off
ParentAdapter        : VMInternalNetworkAdapter, Name = 'Mgmt'
IsTemplate           : True
CimSession           : CimSession: .
ComputerName         : SA18N30-2
IsDeleted            : False

<snip> ...
```

#### <a name="check-mtu-and-jumbo-frame-support-on-hnv-provider-logical-network"></a>Проверка поддержки MTU и кадра, кадры крупных размеров в логической сети поставщика HNV

Другая распространенная проблема в логической сети поставщика HNV является то, что физические сетевые порты и/или Ethernet карты не имеют достаточно большой размер MTU, настроено для обработки дополнительных издержек при инкапсуляции VXLAN (или NVGRE). 
>[!NOTE]
> Некоторые платы Ethernet и драйверы, поддерживающие новое * EncapOverhead ключевое слово, которое автоматически задается значение 160 агент узла сетевого контроллера. Это значение затем добавляется значение * JumboPacket ключевое слово, суммирование используется в качестве объявленных MTU.
> Например * EncapOverhead = 160 и * JumboPacket = 1514 = > MTU = 1674B

```none
# Check whether or not your Ethernet card and driver support *EncapOverhead
PS C:\ > Test-EncapOverheadSettings

Verifying Physical Nic : <NIC> Ethernet Adapter #2
Physical Nic  <NIC> Ethernet Adapter #2 can support SDN traffic. Encapoverhead value set on the nic is  160
Verifying Physical Nic : <NIC> Ethernet Adapter
Physical Nic  <NIC> Ethernet Adapter can support SDN traffic. Encapoverhead value set on the nic is  160
```

Чтобы проверить, независимо от того, имеется ли у логической сети поставщика HNV поддерживает больших MTU размер end-to-end, используйте _LogicalNetworkSupportsJumboPacket теста_ командлета:
```none
# Get credentials for both source host and destination host (or use the same credential if in the same domain)
$sourcehostcred = Get-Credential
$desthostcred = Get-Credential

# Use the Management IP Address or FQDN of the Source and Destination Hyper-V hosts
Test-LogicalNetworkSupportsJumboPacket -SourceHost sa18n30-2 -DestinationHost sa18n30-3 -SourceHostCreds $sourcehostcred -DestinationHostCreds $desthostcred

# Failure Results
SourceCompartment : 3
pinging Source PA: 10.10.182.66 to Destination PA: 10.10.182.64 with Payload: 1632
pinging Source PA: 10.10.182.66 to Destination PA: 10.10.182.64 with Payload: 1472
Checking if physical nics support jumbo packets on host
Physical Nic  <NIC> Ethernet Adapter #2 can support SDN traffic. Encapoverhead value set on the nic is  160
Cannot send jumbo packets to the destination. Physical switch ports may not be configured to support jumbo packets.
Checking if physical nics support jumbo packets on host
Physical Nic  <NIC> Ethernet Adapter #2 can support SDN traffic. Encapoverhead value set on the nic is  160
Cannot send jumbo packets to the destination. Physical switch ports may not be configured to support jumbo packets.

# TODO: Success Results aftering updating MTU on physical switch ports
```

*Исправления*
* Размер MTU на физическом коммутаторе порты должны быть по крайней мере 1674B (включая 14B Ethernet заголовка и окончания)
* Если сетевого адаптера не поддерживает ключевое слово EncapOverhead, измените ключевое слово JumboPacket не менее 1674B


#### <a name="check-tenant-vm-nic-connectivity"></a>Проверка возможности подключения клиента сетевой Адаптер виртуальной Машины
Каждый сетевой Адаптер виртуальной Машины, назначенный гостевой виртуальной Машины имеет ак — АП сопоставление между частного адреса клиента (ак) и пространстве адресов поставщика HNV (PA). Эти сопоставления хранятся в таблицах OVSDB сервера на каждом узле Hyper-V и можно найти, выполнив следующий командлет.

```none
# Get all known PA-CA Mappings from this particular Hyper-V Host
PS > Get-PACAMapping

CA IP Address CA MAC Address    Virtual Subnet ID PA IP Address
------------- --------------    ----------------- -------------
10.254.254.2  00-1D-D8-B7-1C-43              4115 10.10.182.67
10.254.254.3  00-1D-D8-B7-1C-43              4115 10.10.182.67
192.168.1.5   00-1D-D8-B7-1C-07              4114 10.10.182.65
10.254.254.1  40-1D-D8-B7-1C-06              4115 10.10.182.66
192.168.1.1   40-1D-D8-B7-1C-06              4114 10.10.182.66
192.168.1.4   00-1D-D8-B7-1C-05              4114 10.10.182.66
```
>[!NOTE]
> Если сопоставления ак — АП, предполагается, что не выводятся для данного клиента виртуальной Машины, проверьте ресурсов сетевой Адаптер виртуальной Машины и конфигурации IP-адрес для сетевого контроллера с помощью _Get NetworkControllerNetworkInterface_ командлета. Кроме того проверьте установленных подключений между узлами агент узла сетевого Контроллера и сетевом контроллере.

С этой информацией, запрос проверки связи клиента виртуальной Машины может теперь быть инициировано поставщика услуг размещения с помощью сетевого контроллера _VirtualNetworkConnection теста_ командлета.

## <a name="specific-troubleshooting-scenarios"></a>Конкретных сценариев устранения неполадок

Следующие разделы содержат руководство по устранению конкретных сценариев.

### <a name="no-network-connectivity-between-two-tenant-virtual-machines"></a>Отсутствует сетевое подключение между двумя виртуальными машинами клиентов

1.  [Клиент] Убедитесь, что брандмауэр Windows на виртуальных машинах клиента не блокирует трафик.  
2.  [Клиент] Проверьте, что IP-адреса, назначенные виртуальной машине клиента, выполнив _ipconfig_. 
3.  [Поставщика услуг размещения] Запустите **VirtualNetworkConnection теста** из узла Hyper-V, чтобы проверить подключение между виртуальными машинами два клиента в вопросе. 

>[!NOTE]
>VSID ссылается на идентификатор виртуальной подсети В случае VXLAN это идентификатор сети VXLAN (VNI). Это значение можно найти, выполнив **Get PACAMapping** командлета.

#### <a name="example"></a>Пример

    $password = ConvertTo-SecureString -String "password" -AsPlainText -Force
    $cred = New-Object pscredential -ArgumentList (".\administrator", $password) 

Создание ЦС проверки связи между «Зеленый Web VM 1» SenderCA IP-адресом 192.168.1.4; на узле «sa18n30-2.sa18.nttest.microsoft.com» Mgmt IP-адресом 10.127.132.153 ListenerCA IP-адрес из обоих подключенный к виртуальной подсети (VSID) 4114 192.168.1.5.

    Test-VirtualNetworkConnection -OperationId 27 -HostName sa18n30-2.sa18.nttest.microsoft.com -MgmtIp 10.127.132.153 -Creds $cred -VMName "Green Web VM 1" -VMNetworkAdapterName "Green Web VM 1" -SenderCAIP 192.168.1.4 -SenderVSID 4114 -ListenerCAIP 192.168.1.5 -ListenerVSID 4114

    Test-VirtualNetworkConnection at command pipeline position 1

Проверки связи пространстве ак начала запуска сеанса трассировки Ping для 192.168.1.5 успешно с адреса 192.168.1.4 времени приема-передачи = 0 мс


Сведения о маршрутизации ЦС:

    Local IP: 192.168.1.4
    Local VSID: 4114
    Remote IP: 192.168.1.5
    Remote VSID: 4114
    Distributed Router Local IP: 192.168.1.1
    Distributed Router Local MAC: 40-1D-D8-B7-1C-06
    Local CA MAC: 00-1D-D8-B7-1C-05
    Remote CA MAC: 00-1D-D8-B7-1C-07
    Next Hop CA MAC Address: 00-1D-D8-B7-1C-07

Сведения о маршрутизации АП:

    Local PA IP: 10.10.182.66
    Remote PA IP: 10.10.182.65

 <snip> ...

4. [Клиент] Убедитесь, что политики не распределенный брандмауэр, заданные в виртуальную подсеть или сетевых интерфейсов виртуальной Машины, которые блокируют трафик.    

Запрос из демонстрационную среду на sa18n30nc в домене sa18.nttest.microsoft.com REST API сетевого контроллера.

    $uri = "https://sa18n30nc.sa18.nttest.microsoft.com"
    Get-NetworkControllerAccessControlList -ConnectionUri $uri 

# <a name="look-at-ip-configuration-and-virtual-subnets-which-are-referencing-this-acl"></a>Рассмотрим конфигурации IP и виртуальные подсети, который указывает ссылка этого списка ACL

1. [Поставщика услуг размещения] Запустите ``Get-ProviderAddress`` на Hyper-V виртуальным машинам в вопросе клиента размещение двух узлов, а затем запустите ``Test-LogicalNetworkConnection`` или ``ping -c <compartment>`` из узла Hyper-V, чтобы проверить возможность подключения в логической сети поставщика HNV
2.  [Поставщика услуг размещения] Убедитесь, что параметры MTU, правильный на узлах Hyper-V и любом уровня 2 переключения устройства между узлами Hyper-V. Запустите ``Test-EncapOverheadValue`` на всех узлах Hyper-V в вопросе. Также убедитесь, что все параметры уровня 2 между ними MTU, равным как минимум 1674 байтов для максимального использования 160 бит.  
3.  [Поставщика услуг размещения] Если IP-адресов PA не существуют или ЦС соединение разорвано, установите флажок, чтобы убедиться, что получено политики сети. Запустите ``Get-PACAMapping`` для просмотра, если правила инкапсуляцию и сопоставления ак — АП, необходимые для создания виртуальных сетей наложения установлены правильно.  
4.  [Поставщика услуг размещения] Проверьте, что агент узла сетевого контроллера подключен к сетевым контроллером. Запустите ``netstat -anp tcp |findstr 6640`` ли   
5.  [Поставщика услуг размещения] Убедитесь, что идентификатор узла в разделе реестра HKLM / совпадает с Идентификатором экземпляра ресурсов сервера размещения виртуальных машин клиента.  
6. [Поставщика услуг размещения] Идентификатор профиля порта проверьте, соответствует ли идентификатор экземпляра сетевых интерфейсов виртуальной Машины из виртуальных машин клиента.  

## <a name="logging-tracing-and-advanced-diagnostics"></a>Протоколирование, трассировка и расширенная Диагностика

В следующих разделах сведения на расширенную диагностику, ведения журнала и трассировки.

### <a name="network-controller-centralized-logging"></a>Сетевой контроллер централизованное ведение журнала 

Сетевой контроллер можно автоматически собирать журналы отладчика и хранить их в центральном расположении. Сбор журналов можно включить при развертывании сетевого контроллера в первый раз или более поздней версии в любое время. Журналы собираются из сетевого контроллера и сетевых элементов, которыми управляет сетевой контроллер: размещение машин, программные подсистемы балансировки нагрузки (SLB) и машин шлюза. 

В этих журналах содержатся журналы отладки для кластера сетевого контроллера, приложение сетевого контроллера, журналы шлюза, SLB, виртуальные сети и распределенный брандмауэр. При каждом добавлении нового узла/SLB/шлюза сетевого контроллера, ведения журнала запущена на этих компьютерах. Аналогичным образом при узла/SLB или шлюз удален из сетевого контроллера, ведение журнала будет остановлено на этих компьютерах.

#### <a name="enable-logging"></a>Включить ведение журнала

Ведение журналов включается автоматически при установке кластера сетевого контроллера с помощью **Install NetworkControllerCluster** командлета. По умолчанию журналы собираются локально на узлах сетевого контроллера в *%systemdrive%\SDNDiagnostics*. Это **настоятельно рекомендуется** изменить это расположение, чтобы быть удаленных файловых ресурсах (не local). 

Журналы кластера сетевого контроллера, хранятся в *%programData%\Windows Fabric\log\Traces*. Можно указать в централизованное расположение для сбора журналов с **DiagnosticLogLocation** параметр спецификации, согласно которой также быть удаленной общей папке. 

Если вы хотите ограничить доступ к этому расположению, можно указать учетные данные для доступа с **LogLocationCredential** параметра. Если указать учетные данные для доступа к папке журнала, также необходимо предоставить **CredentialEncryptionCertificate** параметр, который используется для шифрования учетных данных, хранящихся локально на узлах сетевого контроллера.  

С параметрами по умолчанию рекомендуется наличие по крайней мере 75 ГБ свободного места в центральном расположении и 25 ГБ на локальных узлах (если не используется центральное расположение) для 3-узлового кластера сетевого контроллера.

#### <a name="change-logging-settings"></a>Изменение параметров ведения журнала

Вы можете изменить параметры ведения журнала в любое время ``Set-NetworkControllerDiagnostic`` командлета. Можно изменить следующие параметры:

- **Централизованное расположение журнала**.  Можно изменить расположение для хранения всех журналов, с помощью ``DiagnosticLogLocation`` параметра.  
- **Учетные данные для доступа к расположению журнала**.  Можно изменить учетные данные для доступа к папке журнала с ``LogLocationCredential`` параметра.  
- **Переместить в локальный журнал**.  Если вы указали централизованное расположение для хранения журналов, можно вернуться к ведение журнала локально на узлах сетевого контроллера с ``UseLocalLogLocation`` параметр (не рекомендуется из-за больших дискового пространства).  
- **Область ведения журнала**.  По умолчанию собираются все журналы. Можно изменить область для сбора журналов кластера только сетевым контроллером.  
- **Уровень ведения журнала**.  Уровень ведения журнала по умолчанию — Informational. Его можно изменить на ошибку, предупреждение или Verbose.  
- **Время существования времени журнала**.  Журналы хранятся в очереди. У вас будет 3 дней ведения журнала данных по умолчанию, при использовании локального ведения журнала или централизованное ведение журнала. Можно изменить это ограничение времени с **LogTimeLimitInDays** параметра.  
- **Время существования размер журнала**.  По умолчанию будет иметь максимальное 75 ГБ данных журналов, при использовании централизованное ведение журнала и 25 ГБ, при использовании локального ведения журнала. Можно изменить это ограничение с **LogSizeLimitInMBs** параметра.

#### <a name="collecting-logs-and-traces"></a>Сбор журналов и трассировки

Развертывание VMM использовать централизованное ведение журнала для сетевого контроллера по умолчанию. Расположение общего ресурса для этих журналов указывается при развертывании шаблона службы сетевого контроллера.

Если расположение файла не указан, локального ведения журнала будет использоваться на каждом узле сетевого контроллера с журналами, сохранен для той C:\Windows\tracing\SDNDiagnostics. Эти журналы сохраняются с помощью следующей иерархии:

- CrashDumps
- NCApplicationCrashDumps
- NCApplicationLogs
- PerfCounters
- SDNDiagnostics
- Трассировки

Сетевой контроллер использует Service Fabric (Azure). Журналы Service Fabric может потребоваться при устранении определенных неполадок. Эти журналы можно найти на каждом узле сетевого контроллера в C:\ProgramData\Microsoft\Service Fabric.

Если пользователь запустит _NetworkController отладки_ командлета, дополнительные журналы будут доступны на каждом узле Hyper-V, который был указан при помощи ресурсом сервера в сетевом контроллере. Эти журналы (и трассировки, если включен), хранятся в разделе C:\NCDiagnostics

### <a name="slb-diagnostics"></a>Диагностика SLB

#### <a name="slbm-fabric-errors-hosting-service-provider-actions"></a>Ошибок структуры SLBM (действия поставщика службы размещения)

1.  Проверьте, что диспетчер подсистемы балансировки нагрузки программного обеспечения (SLBM) работает и что на уровнях оркестрации можно взаимодействовать друг с другом: SLBM "->" SLB/Mux и SLBM -> узлов агентов SLB. Запустите [DumpSlbRestState](https://github.com/Microsoft/SDN/blob/master/Diagnostics/DumpSlbRestState.ps1) с любого узла с доступом к конечной точке REST сетевого контроллера.  
2.  Проверка *SDNSLBMPerfCounters* в системном мониторе на одном из узлов сетевого контроллера виртуальных машин (предпочтительно основной сетевой контроллер узел - Get-NetworkControllerReplica):
    1.  Подключен ли к SLBM ядра подсистемы балансировки нагрузки (LB)? (*SLBM LBEngine конфигурации всего* > 0)  
    2.  SLBM по крайней мере узнает о свои собственные конечные точки? (*Всего виртуального IP-адреса конечных точек* > = 2)  
    3.  Узлы Hyper-V (DIP) подключены к SLBM? (*HP клиентов, подключенных* == num серверы)   
    4.  Подключен ли к Мультиплексорами SLBM? (*Подключенных Мультиплексорами* == *Мультиплексорами работоспособное на SLBM* == *Мультиплексорами reporting работоспособное* = # виртуальные машины Мультиплексорами SLB).  
3.  Убедитесь, что маршрутизатор BGP настроен успешно пиринг с SLB/MUX  
    1.  При использовании RRAS с помощью удаленного доступа (т. е. виртуальная машина BGP):  
        1.  Get-указано должно отображаться подключенных  
        2.  Get-BgpRouteInformation должно отображаться по крайней мере маршрут для SLBM self виртуальных IP-адресов  
    2.  При использовании физических Top-of-Rack (ToR) коммутатора мог выполнять роль узла BGP, обратитесь к документации  
        1.  Например: # Показать экземпляр bgp  
4.  Проверка *SlbMuxPerfCounters* и *SLBMUX* счетчики системного монитора для виртуальной Машины мультиплексора SLB
5.  Проверьте состояние конфигурации и диапазоны виртуальных IP-адресов в Manager подсистемы балансировки нагрузки программного обеспечения Resource  
    1.  Get-NetworkControllerLoadBalancerConfiguration - ConnectionUri < https://<FQDN or IP>| convertto-json-глубина 8 (проверьте диапазонов виртуального IP-адреса в пулы IP-адресов и убедитесь, self SLBM виртуальными IP-Адресами (*LoadBalanacerManagerIPAddress*), а также виртуальные IP-адреса с доступом клиента находятся в этих диапазонах)  
        1. Get-NetworkControllerIpPool - NetworkId «< открытого и закрытого виртуальных IP-адресов логической сети ресурсов ID >» - SubnetId «< открытого и закрытого виртуальных IP-адресов логической подсети идентификатор ресурса >» - ResourceId "<IP Pool Resource Id>" - ConnectionUri $uri | convertto-json-глубина 8 
    2.  Debug-NetworkControllerConfigurationState-  

Если любой из проверок выше сбой, также будет SLB состояние клиента в режим сбоя.  

**Исправления**   
Исходя из следующих диагностические сведения, представленные, исправьте следующее:  
* Убедитесь, что компьютер подключен Мультиплексоры SLB  
  * Устранение проблем сертификата  
  * Исправление сетевых неполадок  
* Убедитесь, что информацию о пиринге BGP успешно настроен.  
* Убедитесь, идентификатор экземпляра сервера в ресурсе сервера соответствует ИД узла в реестре (ссылаться приложение для *HostNotConnected* код ошибки)  
* Собирать журналы  

#### <a name="slbm-tenant-errors-hosting-service-provider--and-tenant-actions"></a>Ошибки клиента SLBM (служба размещения поставщика и клиента действия)

1.  [Поставщика услуг размещения] Проверьте *NetworkControllerConfigurationState отладки* являются ли все ресурсы подсистемы балансировки нагрузки в состоянии ошибки. Попытаемся устранить, выполнив действие элементы таблицы в приложении.   
    1.  Убедитесь, что виртуальный IP-адрес конечной точки присутствует и объявление маршрутов  
    2.  Проверьте, сколько конечных точек выделенного IP-адреса были обнаружены для виртуального IP-адреса конечной точки  
2.  [Клиент] Проверка ресурсов подсистемы балансировки нагрузки указаны правильно  
    1.  Проверка выделенного IP-адреса конечных точек, которые зарегистрированы в SLBM размещаются виртуальные машины клиента, которые соответствуют IP-конфигурации пула адресов серверной части подсистемы балансировки нагрузки  
3.  [Поставщика услуг размещения] Если конечные точки DIP не обнаружен или не подключен:   
    1.  Проверьте *NetworkControllerConfigurationState отладки*  
        1.  Проверка этого сетевого Контроллера и SLB узла агент успешно подключен к координатор событий сетевого контроллера с помощью ``netstat -anp tcp |findstr 6640)``  
    2.  Проверьте *HostId* в *nchostagent* regkey службы (Справочник по *HostNotConnected* код ошибки в приложении) соответствует экземпляру соответствующий ресурс сервера (идентификатор ``Get-NCServer |convertto-json -depth 8``)  
    3.  Убедитесь, что идентификатор профиля порта для порта виртуальной машины соответствует идентификатору экземпляра соответствующей виртуальной машине сетевой КАРТЫ ресурса   
4.  [Поставщик услуг размещения] Сбор журналов   

#### <a name="slb-mux-tracing"></a>Трассировка мультиплексора SLB

Сведения из Мультиплексоров подсистемы балансировки нагрузки программного обеспечения также может определяться через средство просмотра событий. 
1. Щелкните «Показать аналитический и отладочный журналы» в меню «представление средства просмотра событий»
2. Перейдите к «Журналы приложений и служб» > Microsoft > Windows > SlbMuxDriver > трассировки в средстве просмотра событий 
3. Щелкните правой кнопкой и выберите «Включить журнал»

>[!NOTE]
>Рекомендуется иметь только это ведение журнала, активировать в течение некоторого времени, пока вы пытаетесь воспроизведения проблемы

### <a name="vfp-and-vswitch-tracing"></a>VFP и виртуальный коммутатор трассировки

Из Hyper-V размещения, который размещается гостевой виртуальной Машины, подключенные к виртуальной сети клиента, полученный VFP трассировку, чтобы определить, где может быть проблемы.

```
netsh trace start provider=Microsoft-Windows-Hyper-V-VfpExt overwrite=yes tracefile=vfp.etl report=disable provider=Microsoft-Windows-Hyper-V-VmSwitch 
netsh trace stop
netsh trace convert .\vfp.etl ov=yes 
```
