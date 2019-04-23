---
title: Создание подключения поставщика для расширения решения
description: Разработка решения расширения пакета SDK Windows Admin Center (Гонолулу проекта) - создать поставщик подключений
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 09/18/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: 883fba96fcb71cb1c6e8162c1564d66924c4e24d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59885655"
---
# <a name="create-a-connection-provider-for-a-solution-extension"></a>Создание подключения поставщика для расширения решения

>Область применения. Windows Admin Center, предварительная версия Windows Admin Center

Поставщики подключений играют важную роль в том, как Windows Admin Center определяет и взаимодействует с подключаемых объектов или целевых объектов. В первую очередь поставщик подключений выполняет действия, во время попытки подключения, например, гарантируя, что цель — подключен и доступен и гарантировать, что подключающийся пользователь имеет разрешение на доступ к целевой объект.

По умолчанию Windows Admin Center поставляется со следующими поставщиками подключения:

* Server (Сервер)
* Клиент Windows
* Отказоустойчивый кластер
* HCI кластера

Чтобы создать собственный провайдер подключения, выполните следующие действия.

* Добавьте сведения о поставщиках подключения к ```manifest.json```
* Определение поставщика состояния подключения
* Реализация поставщика подключения на уровне приложения

## <a name="add-connection-provider-details-to-manifestjson"></a>Добавление сведений о поставщика подключения в manifest.json

Теперь мы рассмотрим то, что необходимо знать для определения поставщика подключения в вашем проекте ```manifest.json``` файл.

### <a name="create-entry-in-manifestjson"></a>Создание записи в manifest.json

```manifest.json``` Файл расположен в папке \src и содержит, помимо прочего, определения точек входа в проект. Типы точек входа включают средства, решений и поставщики подключений. Мы определим поставщик подключений.

Пример записи поставщика подключения в manifest.json приведен ниже:

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

Точка входа типа «connnectionProvider» обозначает в оболочку Windows Admin Center настраиваемый элемент поставщика, который будет использоваться с помощью решения для проверки состояния подключения. Точки входа для подключения поставщика содержит ряд важных свойств, см. ниже:

| Свойство | Описание |
| -------- | ----------- |
| EntryPointType | Это обязательное свойство. Существует три допустимых значения: «средства», «решение» и «connectionProvider». | 
| name | Идентифицирует поставщика подключения в пределах решения. Это значение должно быть уникальным внутри на полном экземпляре Windows Admin Center (не решения). |
| path | Представляет URL-адрес для «добавить» пользовательского интерфейса подключения, если он будет настроен для решения. Это значение должно соответствовать маршрут, который настраивается в файле routing.module.ts приложения. При настройке решения точку входа для использования подключений rootNavigationBehavior этот маршрут будет загрузить модуль, используемый оболочкой отображать элемент пользовательского интерфейса подключения. Дополнительные сведения доступны в разделе на rootNavigationBehavior. |
| displayName | Введенное здесь значение отображается в правой части оболочки, ниже черную полосу Windows Admin Center при загрузке решения страница "подключения". |
| Значок | Представляет значок, используемый в раскрывающемся меню решения для представления решения. |
| description | Введите краткое описание точки входа. |
| Тип подключения | Представляет тип соединения, который поставщик будет загружаться. Введенное здесь значение будет использоваться в точке входа решения для указания, что решение можно загрузить эти подключения. Введенное здесь значение будет использоваться в средство записи точек для указания, что это средство совместимо с этим типом. Это значение, введенное здесь будет также использоваться в объект соединения, который передан в RPC вызвать «добавить окна», на этапе реализации уровня приложения. |
| connectionTypeName | Используется в таблице подключений для представления соединение, использующее поставщик подключения. Это должен быть во множественном числе имя типа. |
| connectionTypeUrlName | Использовать при создании URL-адрес для представления загруженное решение, после подключения к экземпляру Windows Admin Center. Этот параметр используется, после подключения и перед целевой объект. В этом примере «connectionexample» —, где это значение отображается в URL-адрес: http://localhost:6516/solutionexample/connections/connectionexample/con-fake1.corp.contoso.com |
| connectionTypeDefaultSolution | Представляет компонент по умолчанию, которое должно быть загружено поставщиком подключения. Это значение представляет собой сочетание: [a] Имя пакета расширения, определенные в верхней части манифест. [b] восклицательный знак (!); [c имя точки входа решение.    Для проекта с именем «msft.sme.mySample-extension» и точку входа решения с именем «пример», это значение будет равно «расширение msft.sme.solutionExample! пример». |
| connectionTypeDefaultTool | Представляет значение по умолчанию средство, которое должно быть загружено для успешного подключения. Значение этого свойства состоит из двух частей, аналогичную connectionTypeDefaultSolution. Это значение представляет собой сочетание: [a] Имя пакета расширения, определенные в верхней части манифест. [b] восклицательный знак (!); [c] средство имя точки входа для средства, должны быть загружены изначально. Для проекта с именем «msft.sme.solutionExample-extension» и точку входа решения с именем «пример», это значение будет равно «расширение msft.sme.solutionExample! пример». |
| connectionStatusProvider | Ознакомьтесь с разделом «Определить состояние поставщика подключения» |

## <a name="define-connection-status-provider"></a>Определение поставщика состояния подключения

Поставщик состояния подключения — это механизм, по которому проверяется целевой объект, чтобы быть включен и доступен, гарантировать, что подключающийся пользователь имеет разрешение на доступ к целевой объект. В настоящее время существует два типа поставщиков состояние подключения:  PowerShell и RelativeGatewayUrl.

*   Поставщик состояния подключения PowerShell
    *   Определяет, является ли целевой объект и доступен с помощью сценария PowerShell. Результат должен быть возвращен в объекте с единственным свойством «состояние», см. ниже.
*   Поставщик состояния подключения RelativeGatewayUrl
    *   Определяет, является ли целевой объект и доступен с помощью вызова rest. Результат должен быть возвращен в объекте с единственным свойством «состояние», см. ниже.

### <a name="define-status"></a>Определение состояния

Поставщики состояния соединения являются обязательными для возврата объекта с единственным свойством ```status``` соответствует следующему формату:

``` json
{
    status: {
        label: string;
        type: int;
        details: string;
    }
}
```

Свойства состояния:

* Метка
    * Метка, описывающая состояние возвращаемый тип. Обратите внимание, что значения для метки могут быть сопоставлены в среде выполнения. См. в разделе запись под записью для сопоставления значений в среде выполнения.

* Тип
    * Возвращаемый тип состояния. Тип имеет следующие значения перечисления. Для любого значения 2 или выше платформы, не произойдет переход к присоединенного объекта, и ошибка будет отображаться в пользовательском Интерфейсе.

Типы:

| Значение | Описание |
| ----- | ----------- |
| 0 | Online |
| 1 | Предупреждение |
| 2 | Недостаточно прав |
| 3 | Ошибка |
| 4 | Неустранимая |
| 5 | Неизвестно |

* Подробности
    * Дополнительные сведения, описывающая состояние возвращаемый тип.

### <a name="powershell-connection-status-provider-script"></a>Сценарий PowerShell подключения состояние поставщика

Сценарий PowerShell поставщик состояния подключения определяет, является ли целевой объект и доступен с помощью сценария PowerShell. Результат должен быть возвращен в объекте с единственным свойством — «состояние». Ниже приведен пример сценария.

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

### <a name="define-relativegatewayurl-connection-status-provider-method"></a>Определите метод RelativeGatewayUrl подключения состояние поставщика

Поставщик состояния подключения ```RelativeGatewayUrl``` метод вызывает rest API, чтобы определить, является ли целевой объект и доступен. Результат должен быть возвращен в объекте с единственным свойством — «состояние». Ниже приведен пример записи поставщика подключения в manifest.json RelativeGatewayUrl.

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

* «relativeGatewayUrl» указывает, где можно получить состояние подключения из URL-адрес шлюза. Этот URI задается относительно/API. Если $connectionName обнаруживается в URL-адрес, он будет заменен именем подключения.
* Все свойства relativeGatewayUrl должна выполняться на шлюза узла, что можно выполнить, создав расширение шлюза

### <a name="map-values-in-runtime"></a>Сопоставить значения в среде выполнения

Значения метки и сведений в состояния, возвращаемый объект может быть отформатирован в настроить время, включая ключи и значения в свойстве «defaultValueMap» поставщика.

Например если добавить значение ниже, любое время «defaultConnection_test» отобразилось как значение для метки или сведения Windows Admin Center автоматически заменит ключ строковое значение настроенных ресурсов.

``` json
    "defaultConnection_test": "resources:strings:addServer_status_defaultConnection_label"
```

## <a name="implement-connection-provider-in-application-layer"></a>Реализация поставщика подключения на уровне приложения

Теперь мы собираемся реализовать поставщик подключений на уровне приложения, создав TypeScript класс, реализующий OnInit. Класс имеет следующие функции:

| Функция | Описание |
| -------- | ----------- |
| constructor(private appContextService: AppContextService закрытый маршрута: ActivatedRoute) |  |
| открытый ngOnInit() |  |
| открытый onSubmit() | Содержит логику для обновления оболочки, при попытке подключения добавить |
| открытый onCancel() | Содержит логику для обновления оболочки, при отмене попытки подключения добавить |

### <a name="define-onsubmit"></a>Определите onSubmit

```onSubmit``` проблемы RPC обратный вызов к контексту приложения для оповещения оболочки «Добавление подключения». Базовый вызов использует «updateData» следующим образом:

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

Результатом является свойство соединения, который является массивом объектов, которые соответствуют со следующей структурой:

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

### <a name="define-oncancel"></a>Определите onCancel

```onCancel``` Отменяет попытка «Добавление подключения» при передаче массива пустой подключений:

``` ts
this.appContextService.rpc.updateData(EnvironmentModule.nameOfShell, '##', <RpcUpdateData>{ results: { connections: [] } });
```

## <a name="connection-provider-example"></a>Пример поставщика подключения

Ниже указан полный класс TypeScript для реализации поставщика подключения. Обратите внимание, что строка «connectionType» соответствует «connectionType как определено в поставщика подключения в manifest.json.

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
