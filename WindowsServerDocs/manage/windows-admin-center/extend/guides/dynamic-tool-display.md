---
title: Управление видимостью ваше средство в решении
description: Управление видимостью ваше средство в решении Windows Admin Center SDK (проект Honolulu)
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 09/18/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: f3f34b4c86854bfc55cf4b1b57a0fd3c2baf2ffc
ms.sourcegitcommit: be0144eb59daf3269bebea93cb1c467d67e2d2f1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/20/2018
ms.locfileid: "4080971"
---
# Управление видимостью ваше средство в решении #

>Относится к: Windows Admin Center, ознакомительная версия Windows Admin Center

Могут существовать раз, когда вы хотите исключить (или скрыть) расширения или средство из списка доступных средств. Например если ваше средство предназначено только Windows Server 2016 (не более ранние версии), вы не хотите пользователю, который подключается к серверу Windows Server 2012 R2, чтобы увидеть ваше средство вообще. (Представьте, взаимодействие с пользователем — они щелкните его, подождите, пока средство для загрузки, только для получения сообщений, что его возможности доступны не для их подключения.) Вы можете определить, когда следует отобразить (или скрыть) ваш компонент в файле manifest.json средство.

## Параметры для решения, когда для отображения средства ##

Существует три различные параметры, которые можно использовать для определения, следует ли ваше средство отображаются и доступны для конкретного сервера или кластера подключения.

* localhost
* Инвентаризация (массив свойств)
* сценарий

### LocalHost ###

Свойство localHost объекта условия содержит логическое значение, которое может быть оценено выводить если подключаемый узел localHost (том же компьютере Windows Admin Center на котором установлена), или нет. Передавая значение свойству, когда указания (условие) для отображения инструмента. Например, если требуется только средство для отображения, если пользователь фактически подключение на локальном узле настройте его следующим образом:

``` json
"conditions": [
{
    "localhost": true
}]
```

Кроме того Если ваш инструмент для отображения, когда требуется только подключения *не* узел localhost:

``` json
"conditions": [
{
    "localhost": false
}]
```

Вот как параметры конфигурации выглядеть только средство при подключении узел не является localhost:

``` json
"entryPoints": [
{
    "entryPointType": "tool",
    "name": "main",
    "urlName": "processes",
    "displayName": "resources:strings:displayName",
    "description": "resources:strings:description",
    "icon": "sme-icon:icon-win-serverProcesses",
    "path": "",
    "requirements": [
    {
        "solutionIds": [
        "msft.sme.server-manager!windowsClients"
        ],
        "connectionTypes": [
        "msft.sme.connection-type.windows-client"
        ],
        "conditions": [
        {
            "localhost": true
        }
        ]
    }
    ]
}
```

### Свойства инвентаризации ###

Пакет SDK включает предварительно подобранных наборов перечень свойств, которые можно использовать для создания условия, чтобы определить, когда ваше средство должно быть доступно или нет. Существует девять различных свойств в массиве «запасы».

| Имя свойства | Ожидаемый тип значения |
| ------------- | ------------------- |
| computerManufacturer | string |
| operatingSystemSKU | число |
| operatingSystemVersion | version_string (например: «10.1. *») |
| productType | число |
| Полное_доменное_имя_кластера | string |
| isHyperVRoleInstalled | логический |
| isHyperVPowershellInstalled | логический |
| isManagementToolsAvailable | логический |
| isWmfInstalled | логический |

Каждый объект в массиве инвентаризации должны соответствовать следующей структурой json:

``` json
"<property name>": {
    "type": "<expected type>",
    "operator": "<defined operator to use>",
    "value": "<expected value to evaluate using the operator>"
}
```

#### Оператор значения ####

| Оператор | Описание |
| -------- | ----------- |
| gt | больше |
| GE | больше или равно |
| lt | меньше |
| с низким энергопотреблением | меньше или равно |
| EQ | равным |
| NE | не равно |
|  с помощью  | Проверка, если значение равно true |
| не | Проверка, если значение равно false |
| содержит | элемент существует в строку |
| notContains | элемент не существует в строке |

#### Типы данных ####

Доступные параметры для свойства «тип»:

| Тип | Описание |
| ---- | ----------- |
| version | номер версии (например: 10.1. *) |
| число | числовое значение |
| string | Строковое значение |
| логический | true или false |

#### Типы значений ####

Свойство «value» может принимать следующие типы:

* string
* число
* логический

Набора условий неправильно сформированный инвентаризации выглядит следующим образом:

``` json
"entryPoints": [
{
    "entryPointType": "tool",
    "name": "main",
    "urlName": "processes",
    "displayName": "resources:strings:displayName",
    "description": "resources:strings:description",
    "icon": "sme-icon:icon-win-serverProcesses",
    "path": "",
    "requirements": [
    {
        "solutionIds": [
        "msft.sme.server-manager!servers"
        ],
        "connectionTypes": [
        "msft.sme.connection-type.server"
        ],
        "conditions": [
        {
            "inventory": {
            "operatingSystemVersion": {
                "type": "version",
                "operator": "gt",
                "value": "6.3"
            },
            "operatingSystemSKU": {
                "type": "number",
                "operator": "eq",
                "value": "8"
            }
            }
        }
        ]
    }
    ]
}
```

### Сценарий ###

Наконец можно запустить пользовательский сценарий PowerShell для определения доступности и состояние узла. Все сценарии необходимо вернуть объект со следующей структурой:

``` ps
@{
    State = 'Available' | 'NotSupported' | 'NotConfigured';
    Message = '<Message to explain the reason of state such as not supported and not configured.>';
    Properties =
        @{ Name = 'Prop1'; Value = 'prop1 data'; Type = 'string' },
        @{Name='Prop2'; Value = 12345678; Type='number'; };
}
```
Свойство State имеет важное значение, которое будет управлять принятия решений, чтобы отобразить или скрыть расширения в списке средств.  Допустимые значения::
| Значение | Описание |
| ---- | ----------- |
| Доступно | Расширение должно отображаться в списке "средства". |
| NotSupported | Расширения не должен отображаться в списке "средства". |
| NotConfigured | Это значение-заполнитель для будущих работы, которая запрашивает у пользователя для дополнительной настройки, прежде чем средство становится доступен.  В настоящее время это значение приведет к средство отображается и функциональных эквивалента «Доступно». |

Например если мы хотим средство только в том случае, если удаленный сервер имеет установки BitLocker, сценарий выглядит следующим образом:

``` ps
$response = @{
    State = 'NotSupported';
    Message = 'Not executed';
    Properties = @{ Name = 'Prop1'; Value = 'prop1 data'; Type = 'string' },
        @{Name='Prop2'; Value = 12345678; Type='number'; };
}

if (Get-Module -ListAvailable -Name servermanager) {
    Import-module servermanager; 
    $isInstalled = (Get-WindowsFeature -name bitlocker).Installed;
    $isGood = $isInstalled;
}

if($isGood) {
    $response.State = 'Available';
    $response.Message = 'Everything should work.';
}

$response
```

Настройка точки входа с помощью параметра сценария выглядит следующим образом:

``` json
"entryPoints": [
{
    "entryPointType": "tool",
    "name": "main",
    "urlName": "processes",
    "displayName": "resources:strings:displayName",
    "description": "resources:strings:description",
    "icon": "sme-icon:icon-win-serverProcesses",
    "path": "",
    "requirements": [
    {
        "solutionIds": [
        "msft.sme.server-manager!windowsClients"
        ],
        "connectionTypes": [
        "msft.sme.connection-type.windows-client"
        ],
        "conditions": [
        {
            "localhost": true,
            "inventory": {
            "operatingSystemVersion": {
                "type": "version",
                "operator": "eq",
                "value": "10.0.*"
            },
            "operatingSystemSKU": {
                "type": "number",
                "operator": "eq",
                "value": "4"
            }
            },
            "script": "$response = @{ State = 'NotSupported'; Message = 'Not executed'; Properties = @{ Name = 'Prop1'; Value = 'prop1 data'; Type = 'string' }, @{Name='Prop2'; Value = 12345678; Type='number'; }; }; if (Get-Module -ListAvailable -Name servermanager) { Import-module servermanager; $isInstalled = (Get-WindowsFeature -name bitlocker).Installed; $isGood = $isInstalled; }; if($isGood) { $response.State = 'Available'; $response.Message = 'Everything should work.'; }; $response"
        }
        ]
    }
    ]
}
```

## Поддержка нескольких наборов требование ##

Чтобы определить, когда для отображения ваше средство путем определения нескольких блоков «требования» можно использовать более одного набора требований.

Например, для отображения ваше средство, если «сценарий A» или «сценарий B» имеет значение true, определения двух блоков требования; Если выполняется хотя бы одно (то есть все в блоке требования условий), средство отображается.

``` json
"entryPoints": [
{
    "requirements": [
    {
        "solutionIds": [
            …"scenario A"…
        ],
        "connectionTypes": [
            …"scenario A"…
        ],
        "conditions": [
            …"scenario A"…
        ]
    },
    {
        "solutionIds": [
            …"scenario B"…
        ],
        "connectionTypes": [
            …"scenario B"…
        ],
        "conditions": [
            …"scenario B"…
        ]
    }
    ]
}

```

## Поддержка диапазоны условие ##

Можно также определить диапазон условия путем определения нескольких блоков «условия», в то же свойство, но с помощью различных операторов.

При и то же свойство определяется с помощью различных операторов, средство отображается как значение находится в диапазоне от два условия.

Например это средство отображается как операционная система — версия между 6.3.0 и 10.0.0:

``` json
"entryPoints": [
{
    "entryPointType": "tool",
    "name": "main",
    "urlName": "processes",
    "displayName": "resources:strings:displayName",
    "description": "resources:strings:description",
    "icon": "sme-icon:icon-win-serverProcesses",
    "path": "",
    "requirements": [
    {
        "solutionIds": [
             "msft.sme.server-manager!servers"
        ],
        "connectionTypes": [
             "msft.sme.connection-type.server"
        ],
        "conditions": [
        {
            "inventory": {
                "operatingSystemVersion": {
                    "type": "version",
                    "operator": "gt",
                    "value": "6.3.0"
                },
            }
        },
        {
            "inventory": {
                "operatingSystemVersion": {
                    "type": "version",
                    "operator": "lt",
                    "value": "10.0.0"
                }
            }
        }
        ]
    }
    ]
}

```
