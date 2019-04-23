---
title: Использование пользовательского подключаемого модуля шлюза в расширении средства
description: Разработка модуля средства пакета SDK Windows Admin Center (Гонолулу проекта) - использовать настраиваемый шлюз подключаемый модуль средства расширения
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 09/18/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: c9b2e9201d58472286b42a9c89a36423f40d143d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59834515"
---
# <a name="use-a-custom-gateway-plugin-in-your-tool-extension"></a>Использование пользовательского подключаемого модуля шлюза в расширении средства

>Область применения. Windows Admin Center, предварительная версия Windows Admin Center

В этой статье мы будем использовать подключаемый модуль пользовательского шлюза в расширении инструментов новый, пустой, созданной с помощью интерфейса командной строки Windows Admin Center.

## <a name="prepare-your-environment"></a>Подготовка среды ##

Если это еще не сделано, следуйте указаниям, приведенным в [разрабатывать расширения средство](..\develop-tool.md) для подготовки среды и создайте новый, пустой средства расширения.

## <a name="add-a-module-to-your-project"></a>Добавить модуль в проект ##

Если это еще не сделано, добавьте новый [пустого модуля](add-module.md) в проект, который будет использоваться на следующем шаге.  

## <a name="add-integration-to-custom-gateway-plugin"></a>Добавить настраиваемый шлюз подключаемого модуля интеграции ##

Теперь мы будем использовать подключаемый модуль пользовательского шлюза в новый, пустой модуль, который мы только что создали.

### <a name="create-pluginservicets"></a>Создание plugin.service.ts

Перейдите в каталог нового модуля инструмент, созданный ранее (```\src\app\{!Module-Name}```) и создайте новый файл ```plugin.service.ts```.

Добавьте следующий код в файл, который только что создали:
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

Изменить ссылки на ```Sample Uno``` и ```Sample%20Uno``` к имени функции соответствующим образом.

### <a name="modify-modulets"></a>Изменить module.ts

Откройте ```module.ts``` файл нового модуля, созданного ранее (т. е. ```{!Module-Name}.module.ts```):

Добавьте следующие операторы import:

``` ts
import { HttpService } from '@microsoft/windows-admin-center-sdk/angular';
import { Http } from '@microsoft/windows-admin-center-sdk/core';
import { PluginService } from './plugin.service';
```

Добавьте следующие поставщики (после объявления):

``` ts
  ,
  providers: [
    HttpService,
    PluginService,
    Http
  ]
```

### <a name="modify-componentts"></a>Изменить component.ts

Откройте ```component.ts``` файл нового модуля, созданного ранее (т. е. ```{!Module-Name}.component.ts```):

Добавьте следующие операторы import:

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

Измените параметры конструктора и измените или добавьте следующие функции:

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

### <a name="modify-componenthtml"></a>Изменить component.html ###

Откройте ```component.html``` файл нового модуля, созданного ранее (т. е. ```{!Module-Name}.component.html```):

Добавьте следующее содержимое HTML-файле:
``` html
<button (click)="onClick()" >go</button>
{{ responseResult }}
```

## <a name="build-and-side-load-your-extension"></a>Сборки и на стороне загрузить расширение

Теперь вы готовы к [построения и стороны нагрузки](..\develop-tool.md#build-and-side-load-your-extension) расширения в Windows Admin Center.
