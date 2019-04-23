---
title: Размещение службы вычислений сети (HCN) API для виртуальных машин и контейнеров
description: Узел API службы вычислений сети (HCN) является общедоступным API-интерфейса Win32, предоставляющий доступ на уровне платформы для управления виртуальными сетями, конечные точки виртуальной сети и связанные политики. Вместе это обеспечивает подключения и обеспечения безопасности для виртуальных машин (ВМ) и контейнеров, работающих на узле Windows.
ms.author: jmesser
author: jmesser81
ms.date: 11/05/2018
ms.openlocfilehash: 50af0dab69633aa6e07ded68e9246aa0315377f0
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59844985"
---
# <a name="host-compute-network-hcn-service-api-for-vms-and-containers"></a>Размещение службы вычислений сети (HCN) API для виртуальных машин и контейнеров

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

Узел API службы вычислений сети (HCN) является общедоступным API-интерфейса Win32, предоставляющий доступ на уровне платформы для управления виртуальными сетями, конечные точки виртуальной сети и связанные политики. Вместе это обеспечивает подключения и обеспечения безопасности для виртуальных машин (ВМ) и контейнеров, работающих на узле Windows. 

Разработчики используют API-Интерфейс службы HCN для управления сетей для виртуальных машин и контейнеров в рабочих процессах приложений. HCN API разработано для обеспечения удобства работы для разработчиков. Конечные пользователи не взаимодействуют с этими интерфейсами API напрямую.  

## <a name="features-of-the-hcn-service-api"></a>Функции API службы HCN
-   Реализован в виде размещенной службы сети узла (HNS) на виртуальной Машине/OnCore C API.

-   Предоставляет возможность создания, изменения, удаления и перечисления объектов HCN, например сети, конечные точки, пространства имен и политики. Операции выполняются на дескрипторов к объектам (например, дескриптор сети), а внутри этих маркеров реализуется с помощью дескрипторов контекста RPC.

-   На основе схемы. Большинство функций API-интерфейса определите входные и выходные параметры в виде строк, содержащий аргументы вызова функции в виде документов JSON. Документы JSON основаны на строго типизированным и с версией схемы, эти схемы являются частью общедоступной документации по. 

-   Чтобы клиенты могли зарегистрироваться для уведомлений о событиях уровня службы, например сети выделения и освобождения предоставляется подписка/обратным вызовом API.

-   HCN API работает в мост для классических приложений (так называемые) Centennial) приложения, работающие в системных служб. API проверяет ACL путем получения маркера пользователя из вызывающего объекта.

>[!TIP]
>API-Интерфейс службы HCN поддерживается в фоновые задачи и windows не переднего плана. 

## <a name="terminology-host-vs-compute"></a>Терминология: Узел vs. Вычисления
Службы вычислений узла позволяет вызывающим объектам, для создания и управления виртуальными машинами и контейнерами на одном физическом компьютере. Он называется следовать отраслевой терминологии. 

- **Узел** широко используется в отрасли виртуализации для ссылки в операционную систему, предоставляющий виртуализованные ресурсы.

- **Вычисления** используется для ссылки на методы виртуализации, шире, чем просто виртуальных машин. Вычислительных узлов сетевой службы позволяет вызывающим объектам создавать и управлять ими сети для виртуальных машин и контейнеров на одном физическом компьютере.

## <a name="schema-based-configuration-documents"></a>Документы конфигурации на основе схем
Документы конфигурации на основе четко определенных схем является установленным стандартом отрасли в области виртуализации. Большинство решений виртуализации, такие как Docker и Kubernetes, предоставляют API-интерфейсы на основе конфигурации документов. Отраслевые стандарты, с участием Microsoft, диск экосистему для определения и проверки этих схем, таких как [OpenAPI](https://www.openapis.org/).  Эти инициативы также диска стандартизация определения конкретной схемы для схемы, используемые для контейнеров, таких как [откройте контейнер инициативе Initiative](https://www.opencontainers.org/).

Язык, используемый для создания документов конфигурации является [JSON](https://tools.ietf.org/html/rfc8259), который используется в сочетании с:
-   Определения схемы, которые определяют модель объектов для документа
-   Проверка ли документ JSON на соответствие схеме
-   Автоматическое преобразование документов JSON в собственном представления этих схем в языках программирования, используемые объекты, вызывающие API-интерфейсы и 

Определения часто используемых схемы являются [OpenAPI](https://www.openapis.org/) и [схему JSON](http://json-schema.org/), которые позволяют указать подробные определения свойств в документе, например:
-   Допустимый набор значений для свойства, например 0-100, для свойства, представляющего в процентах.
-   Определение перечисления, которые представлены в виде набора допустимых строк для свойства.
-   Регулярное выражение для ожидаемый формат строки. 

Как часть Документирование API-интерфейсы HCN мы планируем опубликовать схему документы JSON, что спецификации OpenAPI. На основе этой спецификации, можно разрешить конкретного языка представления схемы для использования безопасных типов объектов схемы на языке программирования, используемый клиентом. 

### <a name="example"></a>Пример 

Ниже приведен пример этого рабочего процесса для объект, представляющий SCSI-контроллер в документе конфигурации виртуальной машины. 

В исходном коде Windows, мы определяем схем с использованием файлов .mars: onecore/vm/dv/net/hns/schema/mars/Schema/HCN.Schema.Network.mars

```
enum IpamType
{
    [NewIn("2.0")] Static,
    [NewIn("2.0")] Dhcp,
};

class Ipam
{
    // Type : dhcp
    [NewIn("2.0"),OmitEmpty] IpamType   Type;
    [NewIn("2.0"),OmitEmpty] Subnet     Subnets[];
};

class Subnet : HCN.Schema.Common.Base
{
    [NewIn("2.0"),OmitEmpty] string         IpAddressPrefix;
    [NewIn("2.0"),OmitEmpty] SubnetPolicy   Policies[];
    [NewIn("2.0"),OmitEmpty] Route          Routes[];
};


enum SubnetPolicyType
{
    [NewIn("2.0")] VLAN
};

class SubnetPolicy
{
    [NewIn("2.0"),OmitEmpty] SubnetPolicyType                 Type;
    [NewIn("2.0"),OmitEmpty] HCN.Schema.Common.PolicySettings Data;
};

class PolicySettings
{
    [NewIn("2.0"),OmitEmpty]  string      Name;
};

class VlanPolicy : HCN.Schema.Common.PolicySettings 
{
    [NewIn("2.0")] uint32 IsolationId;
};

class Route 
{
    [NewIn("2.0"),OmitEmpty] string NextHop;
    [NewIn("2.0"),OmitEmpty] string DestinationPrefix;
    [NewIn("2.0"),OmitEmpty] uint16 Metric;
};

```

>[!TIP]
>[Примечания NewIn("2.0") являются частью поддержка управления версиями для определения схемы.

Из этой внутренней определения мы создаем спецификации OpenAPI для схемы:

```
{ 
    "swagger" : "2.0", 
    "info" : { 
       "version" : "2.1", 
       "title" : "HCN API" 
    },
    "definitions": {        
        "Ipam": {
            "type": "object",
            "properties": {
                "Type": {
                    "type": "string",
                    "enum": [
                        "Static",
                        "Dhcp"
                    ],
                    "description": " Type : dhcp"
                },
                "Subnets": {
                    "type": "array",
                    "items": {
                        "$ref": "#/definitions/Subnet"
                    }
                }
            }
        },
        "Subnet": {
            "type": "object",
            "properties": {
                "ID": {
                    "type": "string",
                    "pattern": "^[0-9A-Fa-f]{8}-([0-9A-Fa-f]{4}-){3}[0-9A-Fa-f]{12}$"
                },                
                "IpAddressPrefix": {
                    "type": "string"
                },
                "Policies": {
                    "type": "array",
                    "items": {
                        "$ref": "#/definitions/SubnetPolicy"
                    }
                },
                "Routes": {
                    "type": "array",
                    "items": {
                        "$ref": "#/definitions/Route"
                    }
                }
            }
        },
        "SubnetPolicy": {
            "type": "object",
            "properties": {
                "Type": {
                    "type": "string",
                    "enum": [
                        "VLAN",
                        "VSID"
                    ]
                },
                "Data": {
                    "$ref": "#/definitions/PolicySettings"
                }
            }
        },
        "PolicySettings": {
            "type": "object",
            "properties": {
                "Name": {
                    "type": "string"
                }
            }
        },                      
        "VlanPolicy": {
            "type": "object",
            "properties": {
                "Name": {
                    "type": "string"
                },
                "IsolationId": {
                    "type": "integer",
                    "format": "uint32"
                }
            }
        },
        "Route": {
            "type": "object",
            "properties": {
                "NextHop": {
                    "type": "string"
                },
                "DestinationPrefix": {
                    "type": "string"
                },
                "Metric": {
                    "type": "integer",
                    "format": "uint16"
                }
            }
        }        
    }
} 
```

Можно использовать средства, такие как [Swagger](https://swagger.io/), для создания представлений конкретного языка схемы, используемой клиентом языка программирования. Swagger поддерживает различные языки, такие как C#, Go, Javascript и Python).

- [Созданный пример C# кода](example-c-sharp.md) IPAM верхнего уровня и подсети объекта.

- [Пример кода Go, созданный](example-go.md) IPAM верхнего уровня и подсети объекта. Go используется Docker и Kubernetes, в которой два потребители интерфейсов API службы сети вычислительных узлов. Go имеется встроенная поддержка для маршалинга типов Go в и из документов JSON.

Помимо создания и проверки кода, можно использовать средства для упрощения работы с документами JSON — то есть [Visual Studio Code](https://code.visualstudio.com/Docs/languages/json).

### <a name="top-level-objects-defined-in-the-hcnschemasmars-file"></a>Верхнего уровня объектов, определенных в HCN. Файл schemas.MARS
Как упоминалось выше, можно найти схему документа для документов, используемые API-интерфейсы HCN в наборе файлов .mars под: onecore/виртуальной машины/dv/net/hns / / mars/схемы

Ниже приведены объекты верхнего уровня.
- [HostComputeNetwork](hcn-scenarios.md#scenario-hcn)
- [HostComputeEndpoint](hcn-scenarios.md#scenario-hcn-endpoint)
- [HostComputeNamespace](hcn-scenarios.md#scenario-hcn-namespace)
- [HostComputeLoadBalancer](hcn-scenarios.md#scenario-hcn-load-balancer)

```
class HostComputeNetwork : HCN.Schema.Common.Base
{
    [NewIn("2.0"),OmitEmpty] HCN.Schema.Network.NetworkMode          Type;
    [NewIn("2.0"),OmitEmpty] HCN.Schema.Network.NetworkPolicy        Policies[];
    [NewIn("2.0"),OmitEmpty] HCN.Schema.Network.MacPool              MacPool;
    [NewIn("2.0"),OmitEmpty] HCN.Schema.Network.DNS                  Dns;
    [NewIn("2.0"),OmitEmpty] HCN.Schema.Network.Ipam                 Ipams[];
};

class HostComputeEndpoint : HCN.Schema.Common.Base
{
    [NewIn("2.0"),OmitEmpty] string                                     HostComputeNetwork;
    [NewIn("2.0"),OmitEmpty] HCN.Schema.Network.Endpoint.EndpointPolicy Policies[];
    [NewIn("2.0"),OmitEmpty] HCN.Schema.Network.Endpoint.IpConfig       IpConfigurations[];
    [NewIn("2.0"),OmitEmpty] HCN.Schema.Network.DNS                     Dns;
    [NewIn("2.0"),OmitEmpty] HCN.Schema.Network.Route                   Routes[];
    [NewIn("2.0"),OmitEmpty] string                                     MacAddress;
};

class HostComputeNamespace : HCN.Schema.Common.Base
{
    [NewIn("2.0"),OmitEmpty] uint32                                    NamespaceId;
    [NewIn("2.0"),OmitEmpty] Guid                                      NamespaceGuid;
    [NewIn("2.0"),OmitEmpty] HCN.Schema.Namespace.NamespaceType        Type;
    [NewIn("2.0"),OmitEmpty] HCN.Schema.Namespace.NamespaceResource    Resources[];
};

class HostComputeLoadBalancer : HCN.Schema.Common.Base
{
    [NewIn("2.0"), OmitEmpty] string                                               HostComputeEndpoints[]; 
    [NewIn("2.0"), OmitEmpty] string                                               VirtualIPs[]; 
    [NewIn("2.0"), OmitEmpty] HCN.Schema.Network.Endpoint.Policy.PortMappingPolicy PortMappings[]; 
    [NewIn("2.0"), OmitEmpty] HCN.Schema.LoadBalancer.LoadBalancerPolicy           Policies[];
};
```

## <a name="next-steps"></a>Следующие шаги

- Дополнительные сведения о [распространенные сценарии HCN](hcn-scenarios.md).

- Дополнительные сведения о [обрабатывает контекста RPC для HCN](hcn-declaration-handles.md).

- Дополнительные сведения о [схемы документа HCN JSON](hcn-json-document-schemas.md).