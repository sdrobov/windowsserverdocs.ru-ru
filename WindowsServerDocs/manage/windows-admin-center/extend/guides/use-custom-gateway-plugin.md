---
title: Использование пользовательского подключаемого модуля шлюза в расширении средства
description: Разработка расширения инструмента Windows Admin Center SDK (Project Хонолулу). Использование подключаемого модуля пользовательского шлюза в расширении средства
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 09/18/2018
ms.localizationpriority: medium
ms.prod: windows-server
ms.openlocfilehash: 829cbf6df8cc2738bf4066b36210b860595774ed
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71385227"
---
# <a name="use-a-custom-gateway-plugin-in-your-tool-extension"></a>Использование пользовательского подключаемого модуля шлюза в расширении средства

>Область применения. Windows Admin Center, ознакомительная версия Windows Admin Center

В этой статье мы будем использовать пользовательский подключаемый модуль шлюза в новом, пустом расширении инструмента, созданном с помощью интерфейса командной строки центра администрирования Windows.

## <a name="prepare-your-environment"></a>Подготовка среды ##

Если вы еще этого не сделали, следуйте указаниям в [подсказке по разработке расширения](../develop-tool.md) для подготовки среды и созданию нового пустого расширения инструмента.

## <a name="add-a-module-to-your-project"></a>Добавление модуля в проект ##

Если вы еще этого не сделали, добавьте новый [пустой модуль](add-module.md) в проект, который мы будем использовать на следующем шаге.  

## <a name="add-integration-to-custom-gateway-plugin"></a>Добавление интеграции в пользовательский подключаемый модуль шлюза ##

Теперь мы будем использовать пользовательский подключаемый модуль шлюза в новом пустом модуле, который мы только что создали.

### <a name="create-pluginservicets"></a>Создание подключаемого модуля. Service. TS

Перейдите в каталог нового созданного модуля инструментов (```\src\app\{!Module-Name}```) и создайте новый файл ```plugin.service.ts```.

Добавьте следующий код в только что созданный файл:
``` ts
import { Injectable } from '@angular/core';
import { AppContextService, HttpService } from '@microsoft/windows-admin-center-sdk/angular';
import { Cim, Http, PowerShell, PowerShellSession } from '@microsoft/windows-admin-center-sdk/core';
import { AjaxResponse, Observable } from 'rxjs';

@Injectable()
export class PluginService {
    constructor(private appContextService: AppContextService, private http: Http) {
    }
    
    public getGatewayRestResponse(): Observable<any> {
        let callUrl = this.appContextService.activeConnection.nodeName;

        return this.appContextService.node.get(callUrl, 'features/Sample%20Uno').map(
            (response: any) => {
                return response;
            }
        )
    }
}
```

Измените ссылки на ```Sample Uno``` и ```Sample%20Uno``` на имя функции, как нужно.

[!WARNING]
> Рекомендуется использовать встроенный ```this.appContextService.node``` для вызова любого API, который определен в подключаемом модуле пользовательского шлюза. Это гарантирует, что если в подключаемом модуле шлюза требуются учетные данные, которые будут обрабатываться должным образом.

### <a name="modify-modulets"></a>Изменение модуля. TS

Откройте файл ```module.ts``` созданного ранее модуля (т. е. ```{!Module-Name}.module.ts```):

Добавьте следующие операторы импорта:

``` ts
import { HttpService } from '@microsoft/windows-admin-center-sdk/angular';
import { Http } from '@microsoft/windows-admin-center-sdk/core';
import { PluginService } from './plugin.service';
```

Добавьте следующие поставщики (после объявлений):

``` ts
  ,
  providers: [
    HttpService,
    PluginService,
    Http
  ]
```

### <a name="modify-componentts"></a>Изменение компонента Component. TS

Откройте файл ```component.ts``` созданного ранее модуля (т. е. ```{!Module-Name}.component.ts```):

Добавьте следующие операторы импорта:

``` ts
import { ActivatedRouteSnapshot } from '@angular/router';
import { AppContextService } from '@microsoft/windows-admin-center-sdk/angular';
import { Subscription } from 'rxjs';
import { Strings } from '../../generated/strings';
import { PluginService } from './plugin.service';
```

Добавьте следующие переменные:

``` ts
  private serviceSubscription: Subscription;
  private responseResult: string;
```

Измените конструктор и измените или добавьте следующие функции:

``` ts
  constructor(private appContextService: AppContextService, private plugin: PluginService) {
    //
  }

  public ngOnInit() {
    this.responseResult = 'click go to do something';
  }

  public onClick() {
    this.serviceSubscription = this.plugin.getGatewayRestResponse().subscribe(
      (response: any) => {
        this.responseResult = 'response: ' + response.message;
      },
      (error) => {
        console.log(error);
      }
    );
  }
```

### <a name="modify-componenthtml"></a>Изменение Component. HTML ###

Откройте файл ```component.html``` созданного ранее модуля (т. е. ```{!Module-Name}.component.html```):

Добавьте следующее содержимое в HTML-файл:
``` html
<button (click)="onClick()" >go</button>
{{ responseResult }}
```

## <a name="build-and-side-load-your-extension"></a>Сборка и загрузка на стороне вашего расширения

Теперь все готово для [сборки и загрузки на стороне](../develop-tool.md#build-and-side-load-your-extension) вашего расширения в центре администрирования Windows.
