---
title: Создание поставщика подключения для расширения решения
description: Разработка расширения решения Windows Admin Center SDK (проект Honolulu) — Создание поставщика подключения
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 09/18/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: 883fba96fcb71cb1c6e8162c1564d66924c4e24d
ms.sourcegitcommit: be0144eb59daf3269bebea93cb1c467d67e2d2f1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/20/2018
ms.locfileid: "4081141"
---
# Создание поставщика подключения для расширения решения

>Относится к: Windows Admin Center, ознакомительная версия Windows Admin Center

Поставщики подключения играют важную роль в как Windows Admin Center определяет и взаимодействует с подключаемых объектов или конечных объектов. В первую очередь поставщика подключения выполняет действия во время попытки подключения, например, что делает целевой запущена и доступна, а также гарантируя, что подключаемый пользователь имеет разрешение на доступ к конечному объекту.

По умолчанию Windows Admin Center входит в состав следующих поставщиков подключения:

* Сервер
* Клиент Windows
* Отказоустойчивый кластер
* Кластер HCI

Чтобы создать собственный пользовательский поставщик подключения, выполните следующие действия.

* Добавление сведений о поставщика подключения к ```manifest.json```
* Определите поставщика состояние подключения
* Реализация поставщика подключения на уровне приложения

## Добавление сведений поставщика подключения к manifest.json

Теперь мы ознакомитесь вам нужно знать, чтобы определить поставщик подключения в вашем проекте ```manifest.json``` файла.

### Создайте запись в manifest.json

```manifest.json``` Файл находится в папке \src и содержит, помимо прочего, определения точек входа в свой проект. Типы точек входа включают средства, решения и службы подключения. Мы будем определять поставщика подключения.

Пример записи поставщика подключения в manifest.json используется следующим образом:

``` json
    {
      "entryPointType": "connectionProvider",
      "name": "addServer",
      "path": "/add",
      "displayName": "resources:strings:addServer_displayName",
      "icon": "sme-icon:icon-win-server",
      "description": "resources:strings:description",
      "connectionType": "msft.sme.connection-type.server",
      "connectionTypeName": "resources:strings:addServer_connectionTypeName",
      "connectionTypeUrlName": "server",
      "connectionTypeDefaultSolution": "msft.sme.server-manager!servers",
      "connectionTypeDefaultTool": "msft.sme.server-manager!overview",
      "connectionStatusProvider": {
        "powerShell": {
          "script": "## Get-My-Status ##\nfunction Get-Status()\n{\n# A function like this would be where logic would exist to identify if a node is connectable.\n$status = @{label = $null; type = 0; details = $null; }\n$caption = \"MyConstCaption\"\n$productType = \"MyProductType\"\n# A result object needs to conform to the following object structure to be interpreted properly by the Windows Admin Center shell.\n$result = @{ status = $status; caption = $caption; productType = $productType; version = $version }\n# DO FANCY LOGIC #\n# Once the logic is complete, the following fields need to be populated:\n$status.label = \"Display Thing\"\n$status.type = 0 # This value needs to conform to the LiveConnectionStatusType enum. >= 3 represents a failure.\n$status.details = \"success stuff\"\nreturn $result}\nGet-Status"
        },
        "displayValueMap": {
          "wmfMissing-label": "resources:strings:addServer_status_wmfMissing_label",
          "wmfMissing-details": "resources:strings:addServer_status_wmfMissing_details",
          "unsupported-label": "resources:strings:addServer_status_unsupported_label",
          "unsupported-details": "resources:strings:addServer_status_unsupported_details"
        }
      }
    },
```

Точка входа типа «connnectionProvider» означает в оболочке Windows Admin Center что элемента настроены поставщика, который будет использоваться с помощью решения для проверки состояния подключения. Точки входа поставщик подключения содержит ряд важных свойств, описанной ниже:

| Свойство | Описание |
| -------- | ----------- |
| entryPointType | Это свойство является обязательным. Существует три допустимые значения: «средства», «решения» и «connectionProvider». | 
| name | Определяет поставщика подключения в пределах области решения. Это значение должно быть уникальным внутри полного экземпляра Windows Admin Center (не только решение). |
| path | Представляет пути URL-адреса для «добавить подключение» пользовательского интерфейса, если он будет настроен с помощью решения. Это значение необходимо сопоставить маршрут, который настроен в файле routing.module.ts приложения. Когда точку входа решение настроено для использования rootNavigationBehavior подключения, этот маршрут загрузит модуль, который используется для отображения пользовательского интерфейса подключения добавить оболочкой. Дополнительные сведения доступны в разделе о rootNavigationBehavior. |
| displayName | Здесь введенное значение отображается на правую часть оболочки, ниже черная полоса Windows Admin Center, когда пользователь загружает страницу подключений это решение. |
| icon | Представляет значок, используемый в раскрывающемся меню решения для представления решения. |
| description | Введите краткое описание точку входа. |
| Тип подключения | Представляет тип подключения, которая будет загружать поставщика. Здесь введенное значение будет также использоваться в точку входа решение для указания, что решение можно загрузить эти соединения. Здесь введенное значение будет также использоваться в точках входа средство для указания, что это средство совместимо с этим типом. Это значение, введенные здесь также будет использоваться в объекте подключения, отправленного в RPC вызовов на «добавить окно», на шаге реализации уровня приложения. |
| connectionTypeName | Используется в таблице подключений для представления подключение, которое использует поставщика подключения. Ожидается, что во множественном числе именем типа. |
| connectionTypeUrlName | Используется при создании URL-адрес для представления загруженное решение, после подключения к экземпляру Windows Admin Center. Этот параметр используется, после подключения и перед целевым объектом. В этом примере «connectionexample» —, где это значение отображается в URL-адрес:http://localhost:6516/solutionexample/connections/connectionexample/con-fake1.corp.contoso.com |
| connectionTypeDefaultSolution | Представляет компонент по умолчанию, которое должно быть загружено поставщиком подключения. Это значение представляет собой сочетание: [] — Имя пакета расширения, определенные в верхней части манифест; [b] восклицательный знак (!); [c] решение имя точки входа.    Для проекта с именем «msft.sme.mySample расширением» и точку входа решение с именем «пример», это значение будет «msft.sme.solutionExample расширение! примере». |
| connectionTypeDefaultTool | Представляет по умолчанию средство, которое должно быть загружено на успешного подключения. Значение этого свойства состоит из двух частей, аналогично connectionTypeDefaultSolution. Это значение представляет собой сочетание: [] — Имя пакета расширения, определенные в верхней части манифест; [b] восклицательный знак (!); [c] средство имя точки входа для этого средства, которое должно быть загружено изначально. Для проекта с именем «msft.sme.solutionExample расширением» и точку входа решение с именем «пример», это значение будет «msft.sme.solutionExample расширение! примере». |
| connectionStatusProvider | Ознакомьтесь с разделом «Определить поставщика состояния подключения» |

## Определите поставщика состояние подключения

Поставщик состояния подключения — это механизм, по которому конечный объект проверяется на соответствие запущена и доступна, также гарантируя, что подключаемый пользователь имеет разрешение на доступ к конечному объекту. В настоящее время существует два типа поставщиков состояние подключения: RelativeGatewayUrl и PowerShell.

*   Состояние подключения PowerShell поставщика
    *   Определяет, является ли целевой объект и с помощью сценария PowerShell подключенными к сети. Результат должен быть возвращен в объект с единственным свойством «состояние», описанной ниже.
*   Состояние подключения RelativeGatewayUrl поставщика
    *   Определяет, является ли целевой объект и с помощью вызова rest подключенными к сети. Результат должен быть возвращен в объект с единственным свойством «состояние», описанной ниже.

### Определите состояние

Поставщики состояние подключения, необходимо вернуть объект с единственным свойством ```status``` , соответствует следующий формат:

``` json
{
    status: {
        label: string;
        type: int;
        details: string;
    }
}
```

Состояния свойства:

* Label
    * Метка, описывающая тип возврата состояния. Обратите внимание, что значения для метки могут быть сопоставлены в среде выполнения. См. запись ниже сопоставление значений в среде выполнения.

* Тип
    * Возвращаемый тип состояния. Тип содержит следующие значения перечисления. Любое значение 2 или выше платформа не будет переходить к присоединенного объекта и ошибки будет отображаться в пользовательском Интерфейсе.

Типы:

| Значение | Описание |
| ----- | ----------- |
| 0 | Online |
| 1 | Warning |
| 2 | Unauthorized |
| 3 | Ошибка |
| 4 | Неустранимая |
| 5 | Unknown (неизвестно). |

* Сведения
    * Дополнительные сведения, описывающая состояние возвращаемый тип.

### Сценарий PowerShell поставщика состояние подключения

Сценарий PowerShell поставщика состояния подключения определяет, является ли целевой объект и с помощью сценария PowerShell подключенными к сети. Результат должен быть возвращен в объекта с помощью одного свойства «status». Ниже показан пример сценария.

Пример сценария PowerShell:

``` ts
## Get-My-Status ##

function Get-Status()
{
    # A function like this would be where logic would exist to identify if a node is connectable.
    $status = @{label = $null; type = 0; details = $null; }
    $caption = "MyConstCaption"
    $productType = "MyProductType"

    # A result object needs to conform to the following object structure to be interperated properly by the Windows Admin Center shell.
    $result = @{ status = $status; caption = $caption; productType = $productType; version = $version }

    # DO FANCY LOGIC #

    # Once the logic is complete, the following fields need to be populated:
    $status.label = "Display Thing"
    $status.type = 0 # This value needs to conform to the LiveConnectionStatusType enum. >= 3 represents a failure.
    $status.details = "success stuff"

    return $result
}

Get-Status
```

### Определите метод RelativeGatewayUrl поставщика состояние подключения

Поставщика состояния подключения ```RelativeGatewayUrl``` метод вызывает rest API, чтобы определить, является ли целевой объект и подключенными к сети. Результат должен быть возвращен в объекта с помощью одного свойства «status». Ниже показан пример запись поставщика подключения в manifest.json RelativeGatewayUrl.

``` json
    {
      "entryPointType": "connectionProvider",
      "name": "addServer",
      "path": "/add/server",
      "displayName": "resources:strings:addServer_displayName",
      "icon": "sme-icon:icon-win-server",
      "description": "resources:strings:description",
      "connectionType": "msft.sme.connection-type.server",
      "connectionTypeName": "resources:strings:addServer_connectionTypeName",
      "connectionTypeUrlName": "server",
      "connectionTypeDefaultSolution": "msft.sme.server-manager!servers",
      "connectionTypeDefaultTool": "msft.sme.server-manager!overview",
      "connectionStatusProvider": {
        "relativeGatewayUrl": "<URL here post /api>",
        "displayValueMap": {
          "wmfMissing-label": "resources:strings:addServer_status_wmfMissing_label",
          "wmfMissing-details": "resources:strings:addServer_status_wmfMissing_details",
          "unsupported-label": "resources:strings:addServer_status_unsupported_label",
          "unsupported-details": "resources:strings:addServer_status_unsupported_details"
        }
      }
    },
```

Примечания об использовании RelativeGatewayUrl.

* «relativeGatewayUrl» указывает, где для получения состояния подключения из URL-адрес шлюза. Этот URI является относительным из /api. Если $connectionName можно найти в URL-адрес, он будет заменен имя подключения.
* Все свойства relativeGatewayUrl должен быть выполнен от шлюза узла, который можно достичь путем создания расширения шлюза

### Сопоставление значений в среде выполнения

Значения метки и сведения о состояния, возвращаемого объекта может быть отформатирован в настроить время, включая разделы и значения в свойстве «defaultValueMap» поставщика.

Например при добавлении ниже значения, любое время «defaultConnection_test» показали как значение метки или сведения Windows Admin Center будет автоматически заменить ключ строковое значение настроенных ресурсов.

``` json
    "defaultConnection_test": "resources:strings:addServer_status_defaultConnection_label"
```

## Реализация поставщика подключения на уровне приложения

Теперь мы создадим для реализации поставщика подключения на уровне приложения, путем создания TypeScript класс, реализующий OnInit. Класс имеет следующие функции:

| Функция | Описание |
| -------- | ----------- |
| конструктор (частный appContextService: AppContextService, частный маршрута: ActivatedRoute) |  |
| открытый ngOnInit() |  |
| открытый onSubmit() | Содержит логику для обновления оболочки при попытке подключения добавить |
| открытый onCancel() | Содержит логику для обновления оболочки при отмене попытка добавить подключения |

### Определение onSubmit

```onSubmit``` проблемы RPC обратного вызова для контекста приложения, чтобы уведомить оболочке «добавить подключение». Основные вызов использует «updateData» следующим образом:

``` ts
this.appContextService.rpc.updateData(
    EnvironmentModule.nameOfShell,
    '##',
    <RpcUpdateData>{
        results: {
            connections: connections,
            credentials: this.useCredentials ? this.creds : null
        }
    }
);
```

Результат — это свойство подключения, который является массивом объектов, которые соответствуют следующей структурой:

``` ts

/**
 * The connection attributes class.
 */
export interface ConnectionAttribute {

    /**
     * The id string of this attribute
     */
    id: string;

    /**
     * The value of the attribute. used for attributes that can have variable values such as Operating System
     */
    value?: string | number;
}

/**
 * The connection class.
 */
export interface Connection {

    /**
     * The id of the connection, this is unique per connection
     */
    id: string;

    /**
     * The type of connection
     */
    type: string;

    /**
     * The name of the connection, this is unique per connection type
     */
    name: string;

    /**
     * The property bag of the connection
     */
    properties?: ConnectionProperties;

    /**
     * The ids of attributes identified for this connection
     */
    attributes?: ConnectionAttribute[];

    /**
     * The tags the user(s) have assigned to this connection
     */
    tags?: string[];
}

/**
 * Defines connection type strings known by core
 * Be careful that these strings match what is defined by the manifest of @msft-sme/server-manager
 */
export const connectionTypeConstants = {
    server: 'msft.sme.connection-type.server',
    cluster: 'msft.sme.connection-type.cluster',
    hyperConvergedCluster: 'msft.sme.connection-type.hyper-converged-cluster',
    windowsClient: 'msft.sme.connection-type.windows-client',
    clusterNodesProperty: 'nodes'
};
```

### Определите onCancel

```onCancel``` Отменяет попытка «Добавить подключение», передав массив пустой подключения:

``` ts
this.appContextService.rpc.updateData(EnvironmentModule.nameOfShell, '##', <RpcUpdateData>{ results: { connections: [] } });
```

## Пример поставщика подключения

Полный класс TypeScript для реализации поставщика подключения меньше. Обратите внимание, что строка «тип подключения» соответствует «тип подключения согласно определению в поставщика подключения в manifest.json.

``` ts
import { Component, OnInit } from '@angular/core';
import { ActivatedRoute } from '@angular/router';
import { AppContextService } from '@msft-sme/shell/angular';
import { Connection, ConnectionUtility } from '@msft-sme/shell/core';
import { EnvironmentModule } from '@msft-sme/shell/dist/core/manifest/environment-modules';
import { RpcUpdateData } from '@msft-sme/shell/dist/core/rpc/rpc-base';
import { Strings } from '../../generated/strings';

@Component({
  selector: 'add-example',
  templateUrl: './add-example.component.html',
  styleUrls: ['./add-example.component.css']
})
export class AddExampleComponent implements OnInit {
  public newConnectionName: string;
  public strings = MsftSme.resourcesStrings<Strings>().SolutionExample;
  private connectionType = 'msft.sme.connection-type.example'; // This needs to match the connectionTypes value used in the manifest.json.
  
  constructor(private appContextService: AppContextService, private route: ActivatedRoute) {
    // TODO:
  }

  public ngOnInit() {
    // TODO
  }

  public onSubmit() {
    let connections: Connection[] = [];

    let connection = <Connection> {
      id: ConnectionUtility.createConnectionId(this.connectionType, this.newConnectionName),
      type: this.connectionType,
      name: this.newConnectionName
    };

    connections.push(connection);

    this.appContextService.rpc.updateData(
      EnvironmentModule.nameOfShell,
      '##',
      <RpcUpdateData> {
        results: {
          connections: connections,
          credentials: null
        }
      }
    );
  }

  public onCancel() {
    this.appContextService.rpc.updateData(
      EnvironmentModule.nameOfShell, '##', <RpcUpdateData>{ results: { connections: [] } });
  }
}

```
