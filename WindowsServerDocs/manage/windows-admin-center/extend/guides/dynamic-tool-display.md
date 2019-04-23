---
title: Управлять видимостью этого средства в решении
description: Управлять видимостью этого средства в решении Windows Admin Center SDK (Гонолулу проекта)
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 09/18/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: f3f34b4c86854bfc55cf4b1b57a0fd3c2baf2ffc
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59839255"
---
# <a name="control-your-tools-visibility-in-a-solution"></a>Управлять видимостью этого средства в решении #

>Область применения. Windows Admin Center, предварительная версия Windows Admin Center

Возможны ситуации, когда вы хотите исключить (или скрыть) соответствующего расширения или средства из списка доступных средств. Например если ваше средство предназначено только Windows Server 2016 (не более старых версий), может потребоваться пользователя, который подключается к серверу Windows Server 2012 R2, чтобы увидеть ваше средство вообще. (Представьте себе взаимодействие с пользователем — они Подождите для средства для загрузки, только для того, чтобы получить сообщение, что его возможности доступны не для их подключения, щелкните его.) Можно определить, когда следует отобразить (или скрыть) компонента в файле manifest.json этого средства.

## <a name="options-for-deciding-when-to-show-a-tool"></a>Параметры решения, когда показывать средство ##

Существуют три различные параметры, которые можно использовать для определения, следует ли ваше средство отображаются и доступны для конкретного сервера или подключения к кластеру.

* localhost
* Инвентаризация (массив свойств)
* сценарий

### <a name="localhost"></a>LocalHost ###

Свойство "localHost" объекта условия содержит логическое значение, которое может быть вычислено вывести если подключающийся узел localHost (том же компьютере, установленного на Windows Admin Center) или нет. Передавая значение к свойству, можно указать, когда (условие) для отображения инструмента. Например, если требуется только для отображения, если пользователь на самом деле подключается на локальном узле настройте его следующим образом:

``` json
"conditions": [
{
    "localhost": true
}]
```

Кроме того Если требуется только ваше средство для отображения при подключении узла *не* localhost:

``` json
"conditions": [
{
    "localhost": false
}]
```

Вот, как параметры конфигурации выглядеть Показывать только средство при подключении узла не localhost:

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

### <a name="inventory-properties"></a>Свойства инвентаризации ###

Пакет SDK включает предварительно проверенный набор свойств инвентаризации, которые можно использовать для построения условий, чтобы определить, когда ваше средство должен быть доступен, или нет. Существует девять различных свойств в массиве «инвентаризация».

| Имя свойства | Ожидаемый тип значения |
| ------------- | ------------------- |
| computerManufacturer | строка |
| operatingSystemSKU | number |
| operatingSystemVersion | version_string (например: "10.1.*") |
| productType | number |
| Полное_доменное_имя_кластера | строка |
| isHyperVRoleInstalled | Логический |
| isHyperVPowershellInstalled | Логический |
| isManagementToolsAvailable | Логический |
| isWmfInstalled | Логический |

Каждый объект в массиве инвентаризации должны соответствовать такую структуру json:

``` json
"<property name>": {
    "type": "<expected type>",
    "operator": "<defined operator to use>",
    "value": "<expected value to evaluate using the operator>"
}
```

#### <a name="operator-values"></a>Значения операторов ####

| Оператор | Описание |
| -------- | ----------- |
| gt | Больше |
| GE | Больше или равно |
| lt | Меньше |
| LE | Меньше или равно |
| EQ | Равно |
| NE | Не равно |
| с помощью | проверяется, является ли значение true |
| not | проверяется, является ли значение false |
| Содержит | элемент существует в строке |
| notContains | элемент не существует в строке |

#### <a name="data-types"></a>Типы данных ####

Доступные параметры для свойства «тип»:

| Тип | Описание |
| ---- | ----------- |
| version | номер версии (например: 10.1.*) |
| number | числовое значение |
| строка | Строковое значение |
| Логический | значение true или false |

#### <a name="value-types"></a>Типы значений ####

Свойство «value» принимает следующие типы:

* строка
* number
* Логический

Набора условий инвентаризации правильный формат выглядит следующим образом:

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

### <a name="script"></a>Сценарий ###

Наконец запуском сценария PowerShell для определения доступности и состояние узла. Все сценарии должны возвращать объект со следующей структурой:

``` ps
@{
    State = 'Available' | 'NotSupported' | 'NotConfigured';
    Message = '<Message to explain the reason of state such as not supported and not configured.>';
    Properties =
        @{ Name = 'Prop1'; Value = 'prop1 data'; Type = 'string' },
        @{Name='Prop2'; Value = 12345678; Type='number'; };
}
```
Свойство State имеет важное значение, которое будет управлять принятия решений, чтобы показать или скрыть свое расширение в списке средства.  Допустимыми значениями являются:
| Значение | Описание |
| ---- | ----------- |
| Доступно. | Расширение должно отображаться в списке средств. |
| NotSupported | Расширение не должен отображаться в списке средств. |
| NotConfigured | Это значение заполнителя для дальнейшей работы, который предложит пользователю для дополнительной настройки, прежде чем средство становится доступным.  В настоящее время это значение приведет к в средстве отображения и является функциональным эквивалентом «Доступно». |

Например если нам нужно средство для загрузки только в том случае, если удаленный сервер имеет BitLocker установлены, сценарий выглядит следующим образом:

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

Конфигурацию точки входа, используя параметр скрипта выглядит следующим образом:

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

## <a name="supporting-multiple-requirement-sets"></a>Поддержка нескольких наборов требование ##

Чтобы определить, когда для отображения своего инструмента, определив несколько блоков «требования» можно использовать более одного набора требований.

Например, чтобы отобразить ваше средство, если «сценарий» или «сценарий Б» имеет значение true, определения двух блоков требования; Если выполняется одно (то есть все в блоке требования условий), отображается средство.

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

## <a name="supporting-condition-ranges"></a>Поддержка диапазоны условие ##

Можно также определить различных условий, определив несколько блоков «условия», то же свойство, но с различных операторов.

Если то же свойство определен с помощью различных операторов, средство отображается до тех пор, пока значение находится между двух условий.

Например это средство отображается до тех пор, пока операционная система — это версия 6.3.0 и 10.0.0:

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
