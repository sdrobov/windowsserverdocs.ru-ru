---
title: Изменение типа подключения к кластеру в центре администрирования Windows v1909
description: Изменение типа подключения к кластеру в центре администрирования Windows v1909
ms.technology: manage
ms.topic: article
author: daniellee-msft
ms.author: jol
ms.date: 10/01/2019
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: a07b30517f0d45b7e6f4f41f0ef9a6549e6e2117
ms.sourcegitcommit: de71970be7d81b95610a0977c12d456c3917c331
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952775"
---
# <a name="cluster-connection-type-changes-in-windows-admin-center-v1909"></a>Изменение типа подключения к кластеру в центре администрирования Windows v1909

>Область применения. Windows Admin Center, ознакомительная версия Windows Admin Center

> [!IMPORTANT]
> В этом документе описываются изменения, необходимые разработчикам расширений центра администрирования Windows, которые разрабатывают средства центра администрирования Windows для отказоустойчивого кластера и решений с технологией ХЦИ. Это обязательное изменение, необходимое для того, чтобы ваше расширение было совместимо с предварительной версией Windows Admin Center v1909 и будущих общедоступных выпусков.

В центре администрирования Windows v1909 мы объединены два разных типа подключения к кластеру (отказоустойчивый кластер и подключения к кластеру с поддержкой Hyper-in) в один тип соединения кластера. Пользователям больше не потребуется определять конфигурацию кластера заранее, чтобы выбрать тип подключения для добавления кластера, а также дважды добавить кластер в качестве разных типов соединений, чтобы получить доступ к различным наборам инструментов. Теперь кластеры можно добавить в виде кластера Windows Server, и соответствующие средства будут загружены в основном в зависимости от того, включена ли Локальные дисковые пространства.

Так как это требовало изменения в определении типа соединения и о том, как средства, связанные с кластером, решают, когда следует загружать, расширения, предоставляющие средства для кластеров (ХЦИ или не ХЦИ кластеры или и то и другое), потребуют изменений в реализации, как описано см.

## <a name="manifestjson---solutionsids-and-connectiontypes"></a>manifest. JSON — Солутионсидс и Коннектионтипес

Ранее, чтобы средство отображалось для отказоустойчивого кластера или типа подключения кластера ХЦИ, вы использовали одно из следующих определений в файле ```manifest.json```.

Для отказоустойчивых кластеров:
``` json
    {
        "entryPointType": "tool",
        "name": "MyToolName",
        "urlName": "MyToolUrl",
        "displayName": "MyToolDisplayName",
        "description": "MyToolDescription",
        "icon": "MyToolIcon",
        "path": "MyToolPath",
        "iframeId": "MyToolIframeId",
        "requirements": [
        {
            "solutionIds": [
                "msft.sme.failover-cluster!failover-cluster"
            ],
            "connectionTypes": [
                "msft.sme.connection-type.cluster"
            ]
        }
        ]
    }
```

Для кластеров ХЦИ выделенный выше раздел был бы заменен следующим:
``` json
    "requirements": [
    {
        "solutionIds": [
            "msft.sme.software-defined-data-center!SDDC"
        ],
        "connectionTypes": [
            "msft.sme.connection-type.hyper-converged-cluster"
        ]
    }
    ]
```

В Windows Admin Center 1909 и более поздних версий два Солутионидс и Коннектионтипес были заменены следующими:
``` json
    "requirements": [
    {
        "solutionIds": [
            "msft.sme.software-defined-data-center!cluster"
        ],
        "connectionTypes": [
            "msft.sme.connection-type.cluster"
        ]
    }
    ]
```

Это единственный тип Солутионидс и Коннектионтипес, относящийся к кластеру, поддерживаемый теперь в. Если средство определено только с этим типом Солутионидс и Коннектионтипес, оно будет загружено для любого подключения к отказоустойчивому кластеру независимо от того, является ли он кластером ХЦИ. Если вы хотите ограничить доступ к средству только для кластеров ХЦИ или кластеров, отличных от ХЦИ, необходимо дополнительно использовать новые свойства инвентаризации, описанные в следующем разделе.

## <a name="manifestjson--inventory-properties"></a>manifest. JSON — свойства инвентаризации
При подключении к серверу или кластеру центр администрирования Windows запрашивает набор свойств инвентаризации, которые можно использовать для построения условий, чтобы определить, когда должно быть доступно средство (см. раздел "свойства инвентаризации" в [элементе управления средства ](dynamic-tool-display.md)дополнительные сведения см. в документе о видимости. В центре администрирования Windows v1909 мы добавили в этот список два новых свойства, которые можно использовать для определения того, является ли кластер кластером с поддержкой технологии Hyper-in. 

### <a name="iss2denabled"></a>isS2dEnabled
Технически кластер с поддержкой Hyper-in определяется как отказоустойчивый кластер с включенным Локальные дисковые пространства (S2D). Если вы хотите, чтобы ваше средство было доступно только для кластеров с поддержкой технологии S2D, то, например, при включенной отключении, добавьте следующее условие инвентаризации:
``` json
    "requirements": [
    {
        "solutionIds": [
            "msft.sme.software-defined-data-center!cluster"
        ],
        "connectionTypes": [
            "msft.sme.connection-type.cluster"
        ],
        "conditions": [
        {
            "inventory": {
                "isS2dEnabled": {
                    "type": "boolean",
                    "operator": "is"
                }
            }
        }
        ]
    }
    ]
```
> [!TIP] 
> Если вы хотите, чтобы средство было доступно только в том случае, если функция S2D не включена, измените значение "operator" на "not".

### <a name="isbritannicaenabled"></a>исбританникаенаблед
Кроме того, если вы зависят от ресурса кластера управления SDDC и используете объектную модель SDDC, можно проверить следующее условие:
``` json
    "conditions": [
        {
            "inventory": {
                "isS2dEnabled": {
                    "type": "boolean",
                    "operator": "is"
                },
                "isBritannicaEnabled": {
                    "type": "boolean",
                    "operator": "is"
                }
            }
        }
    ]
```

## <a name="backward-compatibility-to-support-previous-versions-of-windows-admin-center"></a>Обратная совместимость для поддержки предыдущих версий центра администрирования Windows
Чтобы ваше расширение продолжало работать с более старыми версиями центра администрирования Windows, таким как выпуск v1904, предыдущее определение Солутионидс и Коннектионтипес можно использовать вместе с новым определением. См. пример ниже для отображения средства только для кластеров ХЦИ во всех версиях центра администрирования Windows.
``` json
    "requirements": [
    {
        "solutionIds": [
            "msft.sme.software-defined-data-center!SDDC"
        ],
        "connectionTypes": [
            "msft.sme.connection-type.hyper-converged-cluster"
        ]
    },
    {
        "solutionIds": [
            "msft.sme.software-defined-data-center!SDDC",
            "msft.sme.software-defined-data-center!cluster"
        ],
        "connectionTypes": [
            "msft.sme.connection-type.hyper-converged-cluster",
            "msft.sme.connection-type.cluster"
        ],
        "conditions": [
            {
                "inventory": {
                    "isS2dEnabled": {
                        "type": "boolean",
                        "operator": "is"
                    }
                }
            }
        ]
    }
    ]
```

## <a name="known-issue-appcontextserviceactiveconnectionishyperconvergedclusterisfailovercluster-is-not-set-properly-in-windows-admin-center-v1909"></a>Известная проблема: Аппконтекстсервице. activeConnection. Ишиперконвержедклустер/Исфаиловерклустер неправильно задан в Windows Admin Center v1909
Регрессия из последних изменений заключается в том, что свойства ```AppContextService.activeConnection.isHyperConvergedCluster/isFailoverCluster``` не заданы надлежащим образом в центре администрирования Windows v1909 и всегда имеют значение false. Это будет исправлено в следующем выпуске, V1910, но будет нерекомендуемым и больше не станет доступным в общедоступном выпуске 2020. В будущем можно заменить приведенный ниже код и использовать ```this.connectHCI```.
```
    import { ClusterInventoryCache } from '@msft-sme/core';

    constructor(
        ...
        private appContextService: AppContextService,
        ...
    ) {
        ...
        this.clusterInventoryCache = new ClusterInventoryCache(
            this.appContextService,
            <SharedCacheOptions>{ expiration: Constants.sharedCacheExpiration }
        );

         this.isBritannicEnabled().subscribe(result => this.connectHCI = result);
    }

    private isBritannicEnabled(): Observable<boolean> {
        return this.clusterInventoryCache.query(this.getClusterInventoryQueryParameters())
        .pipe(
            map(inventory => {
                return inventory.instance.isBritannicaEnabled;
        }));
    }

    private getClusterInventoryQueryParameters(): ClusterInventoryParams {
        const nodeName = this.appContextService.activeConnection.validNodeName;
        const endpoint = this.appContextService.authorizationManager.getJeaEndpoint(nodeName);
        const options = { powerShellEndpoint: endpoint };
        return {
            name: nodeName,
            requestOptions: options
        };
    }
```