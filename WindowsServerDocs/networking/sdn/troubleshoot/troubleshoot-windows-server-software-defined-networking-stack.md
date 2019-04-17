---
title: Устранение неполадок Windows Server стека программно-конфигурируемой сети
description: Это руководство по Windows Server проверяет распространенных ошибок программно-конфигурируемые сети (SDN) и сценарии сбоев и описываются по устранению неполадок рабочий процесс, который использует доступные средства диагностики.
manager: ravirao
ms.prod: windows-server-threshold
ms.technology: networking-sdn
ms.topic: article
ms.assetid: 9be83ed2-9e62-49e8-88e7-f52d3449aac5
ms.author: pashort
author: JMesser81
ms.openlocfilehash: af59ae6746467f9aecf384d1b3cf9af1e8baeb9a
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="troubleshoot-the-windows-server-software-defined-networking-stack"></a>Устранение неполадок Windows Server стека программно-конфигурируемой сети

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

В этом руководстве рассматриваются наиболее распространенных ошибок программно-конфигурируемые сети (SDN) и сценарии сбоев и описываются по устранению неполадок рабочий процесс, который использует доступные средства диагностики.  

Дополнительные сведения о корпорации Майкрософт, которые определены сетевых программного обеспечения см. в разделе [программного обеспечения определены сети](../../sdn/Software-Defined-Networking--SDN-.md).  

## <a name="error-types"></a>Типы ошибок  
Следующий список представляет класс проблем, наиболее часто возникает с виртуализацией сети Hyper-V (HNVv1) в Windows Server 2012 R2 с имеющиеся на рынке в производственных развертываниях и совпадающим различными способами с теми же типами проблемы в Windows Server 2016 HNVv2 с новым стеком программного обеспечения конфигурируемой сети (SDN).  

Большинство ошибок можно разделить на небольшой набор классов:   
* **Недопустимый или неподдерживаемые конфигурации**  
   Пользователь вызывает северного API-интерфейса неправильно или с недопустимыми политиками.   

* **Ошибка при применении политики**  
     Политики из сетевого контроллера не было доставлено на один узел Hyper-V, значительно задержкой и / или не актуальные на всех узлах Hyper-V (например, после динамической миграции).  
* **Ошибки конфигурации отклонений или программного обеспечения**  
 Путь к данным проблемы приведет к потере пакетов.  

* **Внешние ошибки, относящиеся к оборудованию сетевого Адаптера / драйверов или underlay сеть структуры**  
 Неправильное поведение разгрузки задачи (например, VMQ) или underlay сетевой структуре неправильно (например, MTU)   

 В этом руководстве по устранению неполадок проверяет каждый из этих категорий, ошибки и рекомендует рекомендации и средства диагностики для выявления и устранения ошибки.  

## <a name="diagnostic-tools"></a>Средства диагностики  

Прежде чем обсуждать по устранению неполадок рабочие процессы для каждого из этих типов ошибок, давайте рассмотрим средства диагностики.   
  
Чтобы использовать средства диагностики сети контроллера (элемент управления path), необходимо установить компонент NetworkController средства удаленного администрирования сервера и импортировать ``NetworkControllerDiagnostics``модуля:  

```  
Add-WindowsFeature RSAT-NetworkController -IncludeManagementTools  
Import-Module NetworkControllerDiagnostics  
```  

Для использования средства диагностики HNV диагностики (путь данных), необходимо импортировать ``HNVDiagnostics``модуля:
  
```  
# Assumes RSAT-NetworkController feature has already been installed
Import-Module hnvdiagnostics   
```  

### <a name="network-controller-diagnostics"></a>Средство диагностики контроллера сети  
Эти командлеты описаны на портале TechNet в [раздела командлета диагностики сети контроллера](https://docs.microsoft.com/en-us/powershell/module/networkcontrollerdiagnostics/). Они помогут выявить проблемы согласованности политики сети в элемент управления path между узлами сетевой контроллер и сетевой контроллер и агентов NC узлов, работающих на узлах Hyper-V.

 _ServiceFabricNodeStatus отладки_ и _Get-NetworkControllerReplica_ командлеты необходимо запускать из одного сетевого контроллера узел виртуальных машин. Все диагностические NC командлеты можно запустить с любого узла, который имеет подключение к сетевой контроллер и либо в группе безопасности сети контроллера управления (Kerberos) или имеет доступ к сертификат X.509 для управления сетевым контроллером. 
   
### <a name="hyper-v-host-diagnostics"></a>Диагностика узла Hyper-V  
Эти командлеты описаны на портале TechNet в [раздела командлета диагностики виртуализации сети Hyper-V (HNV)](https://docs.microsoft.com/en-us/powershell/module/hnvdiagnostics/). Они помогают выявлять проблемы в пути к данным между виртуальными машинами клиента (Восток-запад) и входящего трафика через SLB VIP (Север-Юг). 

_VirtualMachineQueueOperation отладки_, _Get-CustomerRoute_, _Get-PACAMapping_, _Get-ProviderAddress_, _Get-VMNetworkAdapterPortId_, _Get VMSwitchExternalPortId_, и _EncapOverheadSettings тестирования_ являются все локальные тестов, которые можно выполнять с любого узла Hyper-V. Другие командлеты вызова тесты пути к данным через сетевой контроллер и поэтому требуется доступ к сетевым контроллером как descried выше.
 
### <a name="github"></a>GitHub
[Репозитории GitHub Microsoft или SDN](https://github.com/microsoft/sdn) имеет ряд примеров сценариев и рабочие процессы, которые сборки на основе этих командлетов в поле. В частности, диагностических сценариев можно найти в [диагностики](https://github.com/Microsoft/sdn/diagnostics) папки. Помогите нам contribute для этих сценариев путем отправки запросов Pull.

## <a name="troubleshooting-workflows-and-guides"></a>Рабочие процессы и руководства по устранению неполадок  

### <a name="hoster-validate-system-health"></a>[Поставщика услуг размещения] Проверки работоспособности системы
Существует внедренного ресурса с именем _состояние конфигурации_ в несколько ресурсов сетевого контроллера. Состояние конфигурации содержит сведения о работоспособности системы, включая согласованность конфигурации сетевого контроллера и фактическое состояние (выполнения) на узлах Hyper-V. 

Чтобы проверить состояние конфигурации, выполните следующее любого узла Hyper-V с подключением к сетевым контроллером.

>[!NOTE] 
>Значение для *NetworkController* параметра должно быть полное доменное имя или IP-адрес, по имени субъекта X.509 > сертификат, созданный для сетевого контроллера.
>
>*Credential* параметра нужно только задать Если сетевого контроллера с помощью проверки подлинности Kerberos (обычно в развертываниях VMM). Необходимо указывать учетные данные для пользователя, который входит в группу безопасности сети контроллера управления.

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

Ниже приводится пример новое сообщение о состоянии конфигурации.

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
> Имеется ошибка в системе, где находятся ресурсы сетевого интерфейса для сетевого Адаптера для виртуальной Машины SLB мультиплексирования пути в состояние ошибки с ошибкой «Виртуального коммутатора — не подключен к контроллера». Эту ошибку можно спокойно проигнорировать, если значение конфигурации IP в ресурсе сетевой Адаптер виртуальной Машины IP-адрес из пула IP-логической сети транспорте. Имеется второй ошибка в системе, где находятся ресурсы сетевого интерфейса для сетевых адаптеров для виртуальных Машин шлюза HNV поставщика в состояние ошибки с ошибкой «PortBlocked — виртуальный коммутатор». Эта ошибка может также безопасно игнорироваться, если для конфигурации IP в ресурсе сетевой Адаптер виртуальной Машины задано значение null (с помощью встроенных).


В таблице ниже перечислены коды ошибок, сообщения и выполнять в зависимости от состояния конфигурации наблюдаемыми дальнейших действий.

  
| **Код**| **Сообщение**| **Действие**|  
|:--------:|:-----------:|----------:|  
| Неизвестно| Неизвестная ошибка| |  
| HostUnreachable                       | Хост-компьютер недоступен | Проверьте подключение к сети управления между сетевой контроллер и узла |  
| PAIpAddressExhausted                  | АП IP-адресов, исчерпана | Увеличить размер пула для логической подсети поставщика HNV IP |  
| PAMacAddressExhausted                 | АП Mac-адресов исчерпана | Увеличьте диапазон пулов Mac |  
| PAAddressConfigurationFailure         | Не удалось выполнить для настройки адреса типа АП на узел | Проверьте сетевое подключение управления между сетевой контроллер и узлом. |  
| CertificateNotTrusted                 | Сертификат не является доверенным  |Исправление сертификаты, используемые для связи с узлом. |  
| CertificateNotAuthorized              | Сертификат не авторизованы | Исправление сертификаты, используемые для связи с узлом. |  
| PolicyConfigurationFailureOnVfp       | Сбой при настройке политики VFP | Это ошибка времени выполнения.  Нет определенного способы. Сбор журналов. |  
| PolicyConfigurationFailure            | Сбой в отправлять политик на узлах, из-за сбоя соединения или другие ошибки в NetworkController.| Никакие определенного действия.  Это связано со сбоем в состоянии цель обработки в модулях сетевого контроллера. Сбор журналов. |  
| HostNotConnectedToController          | Узел еще не подключен сетевой контроллер | Профиль порта, не применяются на узле или узел недоступен из сетевого контроллера. Проверьте, что раздел реестра НомерУзла соответствует Идентификатору экземпляра ресурса сервера |  
| MultipleVfpEnabledSwitches            | Существует несколько VFp коммутаторы включена на узле  | Удалите одну из коммутаторов, поскольку агент узла сетевой контроллер поддерживает только один виртуальный коммутатор с включенным расширением VFP |  
| PolicyConfigurationFailure            | Не удалось выполнить push политики виртуальной сети для VmNic из-за ошибки сертификата и подключение  | Проверьте развернутого необходимых сертификатов (имя субъекта сертификата должно соответствовать полное доменное имя узла). Также проверьте подключение узла с помощью сетевого контроллера |  
| PolicyConfigurationFailure            | Не удалось выполнить push политик виртуальный коммутатор для VmNic из-за ошибки сертификата и подключение  | Проверьте развернутого необходимых сертификатов (имя субъекта сертификата должно соответствовать полное доменное имя узла). Также проверьте подключение узла с помощью сетевого контроллера|
| PolicyConfigurationFailure            | Не удалось выполнить push политик брандмауэра для VmNic из-за ошибки сертификата и подключение | Проверьте развернутого необходимых сертификатов (имя субъекта сертификата должно соответствовать полное доменное имя узла). Также проверьте подключение узла с помощью сетевого контроллера|
| DistributedRouterConfigurationFailure | Не удалось настроить параметры распределенного маршрутизатора на сетевой адаптер узла                          | Ошибка TCPIP стека. Может потребоваться очистка АП и аварийное Восстановление узла виртуальные сетевые карты на сервере, на котором произошла ошибка |
| DhcpAddressAllocationFailure          | Ошибка распределения адресов DHCP для VMNic                                                    | Проверьте, если атрибут статический адрес IP настроен на Сетевых ресурсов |  
| CertificateNotTrusted<br>CertificateNotAuthorized | Не удается подключиться к мультиплексора из-за ошибок сети или сертификатов | Проверьте цифровой код, заданный в коде сообщение об ошибке: это соответствует код ошибки winsock. Сообщения об ошибках сертификатов детальное (например, не удается проверить сертификат, не авторизован сертификата, и т. д.) |  
| HostUnreachable                       | Мультиплексирование — неработоспособно (распространенный случай — BGPRouter отключен) | Узел BGP RRAS (BGP виртуальная машина) или коммутатор верхнего уровня (ToR) недоступен или не пиринга успешно. Проверьте параметры BGP на мультиплексор подсистемы балансировки нагрузки программного обеспечения ресурсов и узла BGP (ToR или RRAS виртуальной машины) |  
| HostNotConnectedToController          | Агент узла SLB не подключен  | Проверьте, что запущена служба агента узла SLB; См. журналы агентом SLB узла (Авто под управлением) по причинам, в случае SLBM (NC) отклонен сертификат, предъявленный агент узла под управлением состояние будет отображать огромным сведения  |  
| PortBlocked                           | Порт VFP заблокирован, из-за отсутствия виртуальной сети или ACL политик | Выясните, существуют другие ошибки, что может стать причиной политик не настраивается. |  
| Перегружен                            | Мультиплексирование Loadbalancer перегружен  | Проблема с производительностью с Мультиплексированием |  
| RoutePublicationFailure               | Мультиплексирование Loadbalancer не подключен к маршрутизатору BGP | Проверьте Если Мультиплексора может соединиться с маршрутизаторами BGP и что пиринга BGP настроен правильно |  
| VirtualServerUnreachable              | Мультиплексирование Loadbalancer не подключен к SLB manager | Проверьте сетевое подключение между SLBM и Мультиплексора |  
| QosConfigurationFailure               | Не удалось настроить политики QOS | Если достаточная пропускная способность доступна для всех виртуальных Машин, если используется резервирование QOS |


#### <a name="check-network-connectivity-between-the-network-controller-and-hyper-v-host-nc-host-agent-service"></a>Проверьте сетевое подключение между сетевой контроллер и узла Hyper-V (служба агента узла NC)
Запустите *netstat* следующую команду для проверки три УСТАНОВЛЕНО подключения между агента узла контекста Именования и узлы сетевой контроллер и один сокета ПРОСЛУШИВАНИЯ на узле Hyper-V
- ПРОСЛУШИВАНИЕ порта TCP:6640 на узле Hyper-V (служба агента узла NC)
- Два установленных подключений из Hyper-V узла IP-порта 6640 на NC узла IP-адресов временных портов (> 32000)
- Один установлено подключение к сети контроллера REST IP-порта 6640 IP-адрес узла Hyper-V на временный порт

>[!NOTE]
>Может существовать только два установленных подключений на узле Hyper-V в случае развертывания на этом конкретном узле виртуальных машин без клиента.

```none
netstat -anp tcp |findstr 6640

# Successful output
  TCP    0.0.0.0:6640           0.0.0.0:0              LISTENING
  TCP    10.127.132.153:6640    10.127.132.213:50095   ESTABLISHED
  TCP    10.127.132.153:6640    10.127.132.214:62514   ESTABLISHED
  TCP    10.127.132.153:50023   10.127.132.211:6640    ESTABLISHED
```
#### <a name="check-host-agent-services"></a>Проверка службы агента узла
Сетевой контроллер взаимодействует с две службы агента узла на узлах Hyper-V: SLB агента узла и агент узла NC. Это возможно, что один или оба этих служб не запущена. Проверьте их состояние и перезапуск, если они не запущены.

```none
Get-Service SlbHostAgent
Get-Service NcHostAgent

# (Re)start requires -Force flag
Start-Service NcHostAgent -Force
Start-Service SlbHostAgent -Force
```

#### <a name="check-health-of-network-controller"></a>Проверьте работоспособность сетевого контроллера
Если не три УСТАНОВЛЕНО подключения или сетевой контроллер отвечать на запросы, проверьте, что все узлы и модули службы запущены и работают с помощью следующих командлетов. 

```none
# Prints a DIFF state (status is automatically updated if state is changed) of a particular service module replica 
Debug-ServiceFabricNodeStatus [-ServiceTypeName] <Service Module>
```
Ниже перечислены модули сетевой контроллер службы
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

Убедитесь, что является ReplicaStatus **готов** и HealthState **ОК**.

В рабочей среде развертывания, с несколькими узлами сетевой контроллер, вы также можете проверить узла основных на каждой службы и его состояние отдельных реплики.

```none  
Get-NetworkControllerReplica

# Sample Output for the API service module
Replicas for service: ApiService

ReplicaRole   : Primary
NodeName      : SA18N30NC3.sa18.nttest.microsoft.com
ReplicaStatus : Ready

```
Убедитесь, что состояние реплики, готовых для каждой службы.
 
#### <a name="check-for-corresponding-hostids-and-certificates-between-network-controller-and-each-hyper-v-host"></a>Проверьте наличие соответствующих HostIDs и сертификатам сетевой контроллер и каждом узле Hyper-V 
На узле Hyper-V выполните следующие команды, чтобы проверить, что НомерУзла соответствует идентификатору экземпляра ресурса сервера сетевого контроллера

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

*Исправление* Если SDNExpress с помощью сценариев или развертывания вручную обновите НомерУзла раздел в реестре в соответствии с идентификатором экземпляра ресурса сервера. Перезапустите агент узла контроллера сети на узле Hyper-V (физическом сервере), если с помощью VMM, удалите сервер Hyper-V в VMM и удалите раздел реестра НомерУзла. Затем снова добавьте на сервере с помощью VMM.


Убедитесь, что отпечатки сертификатов X.509, используемый узлом Hyper-V (имя узла должно быть имя субъекта сертификата) для обмена данными (SouthBound) между узлом Hyper-V (служба агента узла NC) и узлы сетевого контроллера, так же. Также проверьте, имеет имя субъекта сертификата REST сетевой контроллер *CN =<FQDN or IP>*.

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

Вы также можете проверить следующие параметры каждого сертификата, чтобы убедиться, что имя субъекта является ожидаемым (имя узла или NC REST полное доменное имя или IP-), сертификат еще не истек, и всех центров сертификации в цепочке сертификатов включаются в доверенным корневым центром сертификации.

- Имя субъекта  
- Дата окончания срока действия  
- Доверенным корневым центром сертификации  

*Исправление* Если несколько сертификатов имеет то же имя субъекта на узле Hyper-V, агент узла сетевого контроллера случайным образом выбрать один для сетевого контроллера. Это может не соответствовать отпечаток ресурса сервера, известное сетевым контроллером. В этом случае удалите один из сертификатов с одинаковым именем субъекта на узле Hyper-V и повторно запустите службу агента узла сетевого контроллера. Если можно по-прежнему не удается соединение, удалить этот сертификат с тем же именем субъекта, на узле Hyper-V и удалите соответствующий ресурс сервера в VMM. Затем повторно создайте ресурс сервера в VMM, который будет создать сертификат X.509 и установить его на узле Hyper-V.
  

#### <a name="check-the-slb-configuration-state"></a>Проверьте состояние конфигурации SLB
Состояние конфигурации SLB можно определить как часть выходные данные командлету Debug-NetworkController. Этот командлет выводит также текущий набор ресурсов сетевого контроллера в JSON-файлы, все IP-конфигурации с каждого узла Hyper-V (сервер) и политики локальной сети из таблиц базы данных агента узла. 

По умолчанию будет собирать дополнительные трассировки. Чтобы не сбора данных трассировок, добавьте - IncludeTraces: параметр $false.

```none
Debug-NetworkController -NetworkController <FQDN or IP> [-Credential <PS Credential>] [-IncludeTraces:$false]

# Don't collect traces
$cred = Get-Credential 
Debug-NetworkController -NetworkController 10.127.132.211 -Credential $cred -IncludeTraces:$false

Transcript started, output file is C:\\NCDiagnostics.log
Collecting Diagnostics data from NC Nodes
```

>[!NOTE]
>Расположение выходных данных по умолчанию будет directory \NCDiagnostics\ < working_directory >. Выходной каталог по умолчанию можно изменить с помощью `-OutputDirectory`параметра. 

Сведения о состоянии конфигурации SLB можно найти в _диагностики slbstateResults.Json_ файл в этом каталоге.

JSON-файл можно разделить на следующие разделы:
 * Структура
   * SlbmVips — в этом разделе перечислены IP-адрес диспетчера SLB адресов, используемый сетевым контроллером coodinate конфигурации и работоспособности SLB Muxes и SLB узла агентов.
   * MuxState — в этом разделе будут отображаться одно значение для каждого SLB Mux развернуты предоставляя состояние мультиплексора
   * Настройка маршрутизатора — в этом разделе будут отображаться вышестоящего маршрутизатор (узла BGP) номера автономных систем (ASN), время передачи IP-адрес и идентификатор. Он также будут отображаться SLB Muxes ASN и время передачи IP.
   * Подключения узла сведения — в этом разделе списка управления IP-адресов рассматриваются все узлы Hyper-V, доступных для запуска рабочих нагрузок с балансировкой нагрузки.
   * Диапазоны виртуальных IP-адресов — в этом разделе будут отображаться общедоступных и частных диапазоны IP виртуальных IP-адресов пула. SLBM VIP будут добавлены как выделенный IP-адрес из одного из этих диапазонов. 
   * Маршруты мультиплексирования — в этом разделе будут отображаться одно значение для каждого SLB Mux развертывания содержит все объявления маршрутов для этого конкретного мультиплексирования.
 * Клиента
   * VipConsolidatedState - в этом разделе будут отображаться состояние подключения для каждого клиента VIP, включая префикс объявленной маршрута, узла Hyper-V и DIP конечных точек.
    
> [!NOTE]
> Возможно установить состояние SLB напрямую, используя [DumpSlbRestState](https://github.com/Microsoft/SDN/blob/master/Diagnostics/DumpSlbRestState.ps1) сценария на [репозитории Microsoft SDN GitHub](https://github.com/microsoft/sdn). 

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

**От шлюза виртуальной Машины:**
```
Ipconfig /allcompartments /all
Get-NetRoute -IncludeAllCompartments -AddressFamily
Get-NetBgpRouter
Get-NetBgpRouter | Get-BgpPeer
Get-NetBgpRouter | Get-BgpRouteInformation
```

**В верхней части стоечного коммутатора:**

`sh ip bgp summary (for 3rd party BGP Routers)`

**Маршрутизатор BGP Windows**
```
Get-BgpRouter
Get-BgpPeer
Get-BgpRouteInformation
```

Помимо этих из проблем, о которых на данный момент мы видели (особенно в развертываниях на основе SDNExpress) наиболее распространенная причина для секцию клиента не начало настроен на виртуальных машинах GW кажутся тот факт, что емкость GW в FabricConfig.psd1 — меньше по сравнению с жители Попробуйте присвоить сетевых подключений (S2S туннели) в TenantConfig.psd1. Это может быть проверено легко путем сравнения выходные данные из следующих команд:

```
PS > (Get-NetworkControllerGatewayPool -ConnectionUri $uri).properties.Capacity
PS > (Get-NetworkControllerVirtualgatewayNetworkConnection -ConnectionUri $uri -VirtualGatewayId "TenantName").properties.OutboundKiloBitsPerSecond
PS > (Get-NetworkControllerVirtualgatewayNetworkConnection -ConnectionUri $uri -VirtualGatewayId "TenantName").property
```

### <a name="hoster-validate-data-plane"></a>[Поставщика услуг размещения] Проверка плоскости данных
После развертывания сетевого контроллера, были созданы виртуальными сетями и подсети и виртуальные машины были назначены виртуальных подсетей, можно выполнить проверку уровня дополнительные структуры поставщиком услуг размещения для проверки подключения клиента.

#### <a name="check-hnv-provider-logical-network-connectivity"></a>Проверьте подключение к логической сети HNV поставщика
После первой виртуальной машине, Виртуальная машина на узле Hyper-V подключен к виртуальной сети клиента сетевой контроллер назначить двух HNV поставщика IP-адресов (IP-адреса типа АП) для узла Hyper-V. Эти IP-адресов будет получен из пула IP-адресов логической сети HNV поставщика и управляться сетевого контроллера.  Чтобы узнать, каковы эти два IP-адреса HNV

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

Эти HNV поставщика IP-адресов (IP-адреса типа АП), назначаются адаптеров Ethernet, созданные в отдельные секции сети TCPIP и имя адаптера _VLANX_ где X — виртуальной локальной сети, назначенные логической сети HNV поставщика (транспорта).

Связи между двумя узлами Hyper-V с помощью поставщика HNV логической сети можно выполнить, проверку связи с дополнительной секцию (-c Y) параметр, где TCPIP секция сети, в котором создаются PAhostVNICs Y. Это секцию можно определить, выполнив:

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
> АП адаптеров виртуального сетевого адаптера не используется в пути к данным и поэтому не IP-адрес, назначенный адаптеру «vEthernet (PAhostVNic)».

Например предполагается, что узлы Hyper-V 1 и 2 HNV поставщика (АП) IP-адреса:

|Узел hyper-V —|-IP-адрес PA 1|-IP-адрес PA 2|
|---             |---            |---             |
|Узел 1 | 10.10.182.64 | 10.10.182.65 |
|Узел 2 | 10.10.182.66 | 10.10.182.67 |

мы можете проверить связь между ними, используйте следующую команду для проверки связи поставщика HNV логической сети.

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

*Исправление* Если поставщик HNV ping не работает, проверьте подключения к физической сети, включая настройки виртуальной локальной сети. Физические сетевые адаптеры на каждом узле Hyper-V должен быть в режиме магистрали с определенного назначена виртуальная ЛС. Сетевой адаптер узла управления должны быть изолированы для логической сети управления виртуальной локальной сети.

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
 
#### <a name="check-mtu-and-jumbo-frame-support-on-hnv-provider-logical-network"></a>Проверка поддержки MTU и кадров крупного размера в логической сети, поставщик HNV

Другая общая проблема в логической сети HNV поставщика является порты физической сети и/или адаптер Ethernet не достаточно большой MTU настроен для обработки издержек, связанных с инкапсуляция VXLAN (или NVGRE). 
>[!NOTE]
> Некоторые карты Ethernet и драйверы поддерживают новые * EncapOverhead ключевое слово, которое будет установлен автоматически агент узла сетевого контроллера значение 160. Это значение затем можно добавить к значению * ключевое слово JumboPacket которого объяснение используется в качестве объявленной MTU.
> Например * EncapOverhead = 160 и * JumboPacket = 1514 = > MTU = 1674B

```none
# Check whether or not your Ethernet card and driver support *EncapOverhead
PS C:\ > Test-EncapOverheadSettings

Verifying Physical Nic : <NIC> Ethernet Adapter #2
Physical Nic  <NIC> Ethernet Adapter #2 can support SDN traffic. Encapoverhead value set on the nic is  160
Verifying Physical Nic : <NIC> Ethernet Adapter
Physical Nic  <NIC> Ethernet Adapter can support SDN traffic. Encapoverhead value set on the nic is  160
```

Чтобы проверить ли логической сети HNV поставщик поддерживает больших MTU размер узел узел, используйте _теста LogicalNetworkSupportsJumboPacket_ командлета:
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
* Изменить размер MTU на физические порты коммутатора не менее 1674B (включая заголовка Ethernet 14B и анонс)
* Если сетевого адаптера не поддерживает ключевое слово EncapOverhead, настройте ключевое JumboPacket быть по крайней мере 1674B


#### <a name="check-tenant-vm-nic-connectivity"></a>Проверьте подключение к сетевой Адаптер виртуальной Машины клиента
Каждый сетевой Адаптер виртуальной Машины, назначенные гостевой виртуальной Машины имеет сопоставления ак — АП частного адреса клиента (ак) и пространства адресов HNV поставщика (АП). Эти сопоставления хранятся в таблицах OVSDB server на каждом узле Hyper-V и может быть найден, выполнив следующий командлет.

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
> Если сопоставления ак — АП, предполагается, что не выводятся для конкретного клиента виртуальной Машины, проверьте ресурсы сетевой Адаптер виртуальной Машины и конфигурации IP для сетевого контроллера с помощью _Get-NetworkControllerNetworkInterface_ командлета. Кроме того проверьте установленных подключений между узлами NC агента узла и сетевой контроллер.

С этой информацией, запрос проверки связи виртуальной Машины клиента могут вызываться теперь поставщика услуг размещения с помощью сетевого контроллера _тест VirtualNetworkConnection_ командлета.

## <a name="specific-troubleshooting-scenarios"></a>В определенных сценариях устранения неполадок

В следующих разделах приводятся рекомендации по устранению конкретных сценариев.

### <a name="no-network-connectivity-between-two-tenant-virtual-machines"></a>Нет сетевого подключения между двумя виртуальные машины клиента

1.  [Клиент] Убедитесь, что брандмауэр Windows в виртуальные машины клиента не блокирует трафик.  
2.  [Клиент] Проверьте, что IP-адресов были назначены виртуальной машины клиента, выполнив _ipconfig_. 
3.  [Поставщика услуг размещения] Запустите **тест VirtualNetworkConnection** с узла Hyper-V для проверки подключения между виртуальными машинами два клиента в вопросе. 

>[!NOTE]
>VSID ссылается на идентификатор виртуальной подсети В случае VXLAN это идентификатор сети VXLAN (VNI). Это значение можно найти, выполнив **Get-PACAMapping** командлета.

#### <a name="example"></a>Пример

    $password = ConvertTo-SecureString -String "password" -AsPlainText -Force
    $cred = New-Object pscredential -ArgumentList (".\administrator", $password) 

Создайте ЦС проверки связи между «Web зеленого виртуальной Машины 1» с IP-адрес SenderCA 192.168.1.4 на узле «sa18n30-2.sa18.nttest.microsoft.com» с IP-Mgmt 10.127.132.153 для ListenerCA IP-адреса из 192.168.1.5 подключенные к виртуальной подсети (VSID) 4114.

    Test-VirtualNetworkConnection -OperationId 27 -HostName sa18n30-2.sa18.nttest.microsoft.com -MgmtIp 10.127.132.153 -Creds $cred -VMName "Green Web VM 1" -VMNetworkAdapterName "Green Web VM 1" -SenderCAIP 192.168.1.4 -SenderVSID 4114 -ListenerCAIP 192.168.1.5 -ListenerVSID 4114

    Test-VirtualNetworkConnection at command pipeline position 1

Запуск ЦС пространства пакетами запуск сеанса трассировки Ping для 192.168.1.5 успешно с адреса 192.168.1.4 времени приема-передачи = 0 ms


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

4.  [Клиент] Убедитесь, что политики не распределением брандмауэра, указанная в виртуальной подсети или виртуальной Машины сетевых интерфейсов, которые бы блокируют трафик.    

Запрос найден в среде Демонстрация в sa18n30nc в домене sa18.nttest.microsoft.com REST API сетевого контроллера.

    $uri = "https://sa18n30nc.sa18.nttest.microsoft.com"
    Get-NetworkControllerAccessControlList -ConnectionUri $uri 

# <a name="look-at-ip-configuration-and-virtual-subnets-which-are-referencing-this-acl"></a>Посмотрите на IP-конфигурации и виртуальные подсети, который ссылаетесь на этот ACL

1. [Поставщика услуг размещения] Запустите ``Get-ProviderAddress``на обоих Hyper-V размещения двух узлов виртуальных машин в вопросе клиента, а затем запустите ``Test-LogicalNetworkConnection``или ``ping -c <compartment>``с узла Hyper-V для проверки подключения в логической сети HNV поставщика
2.  [Поставщика услуг размещения] Убедитесь, что параметры MTU настроены правильно на узлах Hyper-V и все уровня 2 Переключение устройств между узлами Hyper-V. Запустите ``Test-EncapOverheadValue``на всех узлах Hyper-V в вопросе. Также убедитесь, что все коммутаторы 2-го уровня в между предоставлены MTU задана как минимум 1674 байт с максимальной нагрузки 160 бит.  
3.  [Поставщика услуг размещения] Если IP-адреса типа АП отсутствуют или разрыве подключения ЦС, проверьте убедитесь, что был получен политики сети. Запустите ``Get-PACAMapping``для просмотра, если правила инкапсуляция и сопоставления ак — АП, необходимые для создания виртуальных сетей наложения, правильно настроены.  
4.  [Поставщика услуг размещения] Убедитесь, что агент узла сетевой контроллер подключен к сетевым контроллером. Запустите ``netstat -anp tcp |findstr 6640``ли   
5.  [Поставщика услуг размещения] Убедитесь, что идентификатор узла в HKLM или совпадает с Идентификатором экземпляра ресурсов сервера размещения виртуальных машин клиента.  
6. [Поставщика услуг размещения] Проверяет, что идентификатор профиля порта соответствует идентификатор экземпляра интерфейсов сети виртуальных Машин, виртуальных машин клиента.  

## <a name="logging-tracing-and-advanced-diagnostics"></a>Ведение журнала, трассировки и расширенной диагностики

Следующие разделы содержат сведения о расширенной диагностике, ведение журнала и трассировка.

### <a name="network-controller-centralized-logging"></a>Сетевой контроллер централизованное ведение журнала 
 
Сетевой контроллер может автоматически собирать журналы отладчик и хранить их в центральном расположении. Сбор данных журнала можно включить, если при развертывании сетевого контроллера в первый раз или более поздней версии в любое время. Журналы, собранные с помощью сетевого контроллера и сетевых элементы управляется сетевого контроллера: размещена компьютеров, программное обеспечение подсистем балансировки нагрузки (SLB) и машин шлюза. 

Эти журналы включают журналы отладки кластера сетевой контроллер, сетевой контроллер приложения, шлюза журналов, SLB, виртуальных сетей и распределением брандмауэра. Каждый раз, когда новый узел и SLB/шлюз добавляется сетевой контроллер, на этих компьютерах запуске ведения журнала. Аналогично при удалении узла SLB/шлюза или из сетевого контроллера ведение журнала остановлено на этих компьютерах.

#### <a name="enable-logging"></a>Включить ведение журнала

Ведение журнала включено автоматически при установке кластера сетевого контроллера с помощью **установки NetworkControllerCluster** командлета. По умолчанию журналы собираются локально на узлах сетевой контроллер на *%systemdrive%\SDNDiagnostics*. Это **настоятельно рекомендуется** изменении расположения быть удаленном файловом ресурсе (не local). 

Журналы кластера сетевой контроллер сохраняются в *%programData%\Windows Fabric\log\Traces*. Можно указать для централизованного сбора журналов с **DiagnosticLogLocation** параметр рекомендациям, это также быть удаленном файловом ресурсе. 

Если вы хотите ограничить доступ в этом расположении, можно предоставлять учетные данные с **LogLocationCredential** параметра. Если указать учетные данные для доступа к папке журнала, также следует указать **CredentialEncryptionCertificate** параметр, который используется для шифрования учетных данных, хранящихся локально на узлах сетевого контроллера.  

С параметрами по умолчанию рекомендуется наличие по крайней мере 75 ГБ свободного пространства в центральном расположении и 25 ГБ на локальных узлов (если не используется в центральном расположении) для сетевого контроллера 3 узел кластера.

#### <a name="change-logging-settings"></a>Изменить параметры ведения журнала

Вы можете изменить параметры ведения журнала во время с помощью ``Set-NetworkControllerDiagnostic``командлета. Можно изменить следующие параметры:

- **Централизованное расположение журнала**.  Можно изменить расположение для хранения всех журналов с ``DiagnosticLogLocation``параметра.  
- **Учетные данные, чтобы получить доступ к папке журнала**.  Вы можете изменить учетные данные для доступа к папке журнала с ``LogLocationCredential``параметра.  
- **Переместите локальный ведения журнала**.  Если вы указали централизованное расположение для хранения журналов, можно будет переместить обратно локально входить на узлах сетевого контроллера с ``UseLocalLogLocation``параметра (не рекомендуется из-за больших дискового пространства).  
- **Ведение журнала область**.  По умолчанию собираются все журналы. Можно изменить область для сбора журналов кластера только сетевым контроллером.  
- **Уровень ведения журнала**.  Уровень ведения журнала по умолчанию — информационное сообщение. Ошибка, предупреждение или Verbose можно изменить.  
- **Время время существования журнала**.  Журналы сохраняются по кругу. Вы получите 3 дня данные ведения журнала по умолчанию при использовании локального ведения журнала или централизованное ведение журнала. Вы можете изменить этот лимит с **LogTimeLimitInDays** параметра.  
- **Время существования размер журнала**.  По умолчанию будет иметь максимальное 75 ГБ данных ведения журнала, если с помощью централизованное ведение журналов и 25 ГБ, при использовании локального ведения журнала. Вы можете изменить этот предел с **LogSizeLimitInMBs** параметра.

#### <a name="collecting-logs-and-traces"></a>Сбор журналов и трассировок

Развертывание VMM использовать централизованное ведение журнала для сетевого контроллера по умолчанию. При развертывании шаблона службы сетевой контроллер, указывается расположение общего ресурса для этих журналов.

Если расположение файла не было задано, локального ведения журнала будет использоваться на каждом узле сетевого контроллера с помощью журналов, сохраненные в разделе C:\Windows\tracing\SDNDiagnostics. Эти журналы, сохраняются с помощью следующей иерархии:

- CrashDumps
- NCApplicationCrashDumps
- NCApplicationLogs
- PerfCounters
- SDNDiagnostics
- Трассировок

Сетевой контроллер использует Service Fabric (Azure). Журналы Service Fabric может потребоваться при устранении неполадок определенные проблемы. Эти журналы можно найти на каждом узле сетевого контроллера в C:\ProgramData\Microsoft\Service структуры.

Если пользователь был запущен _отладки NetworkController_ командлета, будут доступны дополнительные журналы на каждом узле Hyper-V, который был указан при server ресурс в сетевой контроллер. Эти журналы (и трассировок, если параметр включен) хранятся в разделе C:\NCDiagnostics

### <a name="slb-diagnostics"></a>Диагностика SLB

#### <a name="slbm-fabric-errors-hosting-service-provider-actions"></a>Ошибки SLBM структуры (действия поставщика служб размещения)

1.  Проверьте, что диспетчер балансировки нагрузки программного обеспечения (SLBM) работает и что слои согласование может взаимодействовать друг с другом: SLBM -> SLB Mux и SLBM -> SLB агентов узлов. Запустите [DumpSlbRestState](https://github.com/Microsoft/SDN/blob/master/Diagnostics/DumpSlbRestState.ps1) с любого узла с доступом к конечной точке REST сетевого контроллера.  
2.  Проверка *SDNSLBMPerfCounters* в системном мониторе на одном узле контроллера сети виртуальных машин (предпочтительно основного сетевого контроллера узел - Get-NetworkControllerReplica):
    1.  Подсистема балансировки нагрузки (Фунтов) подключен SLBM? (*Всего конфигураций SLBM LBEngine* > 0)  
    2.  SLBM по крайней мере узнает о собственный конечных? (*Виртуальных IP-адресов конечных точек всего* > = 2)  
    3.  Узлы Hyper-V (DIP) подключены SLBM? (*Подключенных клиентов HP* == num серверов)   
    4.  Подключен ли SLBM Muxes? (*Подключен Muxes* == *Muxes работоспособного на SLBM* == *Muxes отчетов работоспособное* = # виртуальные машины Muxes SLB).  
3.  Убедитесь, что маршрутизатор BGP настроена успешно пиринг с SLB MUX  
    1.  При использовании службы RRAS с помощью удаленного доступа (т. е. BGP виртуальная машина):  
        1.  Get-BgpPeer должно отображаться подключением  
        2.  Get-BgpRouteInformation должно отображаться по крайней мере маршрут для SLBM self виртуальных IP-адресов  
    2.  При использовании физических верхнего уровня (ToR) коммутатора как узла BGP, обратитесь к документации  
        1.  Например: # Показать экземпляра bgp  
4.  Проверка *SlbMuxPerfCounters* и *SLBMUX* счетчики системного монитора на виртуальной Машине мультиплексора SLB
5.  Проверьте состояние конфигурации и диапазоны виртуальных IP-адресов в ресурсе диспетчер балансировки нагрузки программного обеспечения  
    1.  Get-NetworkControllerLoadBalancerConfiguration - ConnectionUri < https://<FQDN or IP>| ConvertTo-json-глубины 8 (проверьте диапазон виртуальных IP-адресов в пулы IP-адресов и убедитесь, SLBM self-VIP (*LoadBalanacerManagerIPAddress*) и все стороне клиента виртуальные IP-адреса находятся в пределах этих диапазонов)  
        1. Get-NetworkControllerIpPool - NetworkId «< открытого и закрытого виртуальных IP-адресов логической сети идентификатор ресурса >» - SubnetId «< открытого и закрытого виртуальных IP-адресов логической подсети идентификатор ресурса >» - ResourceId «<IP Pool Resource Id>» - ConnectionUri $uri | convertto-json-глубины 8 
    2.  Debug-NetworkControllerConfigurationState-  

Если любой из проверок выше сбой, в режиме сбоя также будет SLB состояния клиента.  

**Исправления**   
В зависимости от следующие диагностические сведения, представленные исправьте следующее:  
* Убедитесь, что подключены Мультиплексоры SLB  
  * Устранение проблем с сертификатом  
  * Устранение сетевых неполадок  
* Убедитесь, что сведения пиринга BGP успешно настроена  
* Соответствовала идентификатор узла в реестре идентификатор экземпляра сервера в Server ресурс (в приложении *HostNotConnected* код ошибки)  
* Сбор журналов  

#### <a name="slbm-tenant-errors-hosting-service-provider--and-tenant-actions"></a>Ошибки SLBM клиента (служба размещения поставщика и клиента действия)

1.  [Поставщика услуг размещения] Проверьте *отладки NetworkControllerConfigurationState* для просмотра, если все ресурсы LoadBalancer находятся в состоянии ошибки. Попробуйте уменьшить, выполнив действие элементы таблицы в приложении.   
    1.  Убедитесь, что конечную точку виртуальных IP-адресов, отсутствуют, а маршруты рекламы  
    2.  Проверьте, сколько DIP конечных точек, обнаруженных для конечной точки виртуальных IP-адресов  
2.  [Клиент] Проверка ресурсов подсистемы балансировки нагрузки указаны правильно  
    1.  Проверка DIP конечных точек, которые зарегистрированы в SLBM размещены виртуальные машины клиента, которые соответствуют пула IP-адрес LoadBalancer внутренними конфигурации  
3.  [Поставщика услуг размещения] Если конечные точки DIP не обнаружены или не подключенных:   
    1.  Проверьте *NetworkControllerConfigurationState отладки*  
        1.  Проверить, NC и агент узла SLB будет успешно установлено соединение с помощью сетевого контроллера событий координатора ``netstat -anp tcp |findstr 6640)``  
    2.  Проверьте *НомерУзла* в *nchostagent* regkey службы (Справочник по *HostNotConnected* код ошибки в приложении) соответствует идентификатор экземпляра соответствующий ресурс сервера (``Get-NCServer |convertto-json -depth 8``)  
    3.  Убедитесь, что соответствующий ресурс виртуальной машины сетевого Адаптера идентификатор экземпляра соответствует ИД профиль порта для порта виртуальной машины   
4.  [Поставщик размещения] Сбор журналов   

#### <a name="slb-mux-tracing"></a>SLB мультиплексирования трассировки

Сведения из Muxes подсистемы балансировки нагрузки программного обеспечения также можно определить при помощи средства просмотра событий. 
1. Щелкните «Отобразить аналитический и отладочный журналы» в меню представление средства просмотра событий
2. Перейдите в «Журналы приложений и служб» > Microsoft > Windows > SlbMuxDriver > трассировки в средстве просмотра событий 
3. Щелкните его правой кнопкой мыши и выберите «Включить журнал»

>[!NOTE]
>Рекомендуется только есть запись включена на короткое время, когда вы пытаетесь воспроизвести проблему

### <a name="vfp-and-vswitch-tracing"></a>VFP и трассировка виртуальный коммутатор

Из Hyper-V узла, который размещается в гостевой ВМ, подключенных к виртуальной сети клиента, можно собирать VFP трассировку, чтобы определить, где может находиться проблемы.

```
netsh trace start provider=Microsoft-Windows-Hyper-V-VfpExt overwrite=yes tracefile=vfp.etl report=disable provider=Microsoft-Windows-Hyper-V-VmSwitch 
netsh trace stop
netsh trace convert .\vfp.etl ov=yes 
```
