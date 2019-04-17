---
title: Использование пользовательского подключаемого модуля шлюза в расширении средства
description: Разработка расширения средства Windows Admin Center SDK (проект Honolulu) — использовать подключаемый модуль пользовательских шлюза в расширении средство
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 09/18/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: 4652616478b7b05bde97db48bf84648984b5a325
ms.sourcegitcommit: f1edfc6525e09dd116b106293f9260123a94de0c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "9296766"
---
# Использование пользовательского подключаемого модуля шлюза в расширении средства

>Относится к: Windows Admin Center, ознакомительная версия Windows Admin Center

В этой статье мы будем использовать подключаемый модуль пользовательских шлюза в расширении новый пустой средство, которые мы создали с помощью Windows Admin Center CLI.

## Подготовка среды ##

Если вы еще не сделали этого, следуйте инструкциям в [разработке расширения средства](..\develop-tool.md) подготовить среду и создать новый, пустой средство расширения.

## Добавление модуля в проект ##

Если вы еще не сделали этого, добавьте новый [пустой модуль](add-module.md) в свой проект, который мы будем использовать его на следующем шаге.  

## Добавление подключаемого модуля шлюза пользовательских интеграции ##

Теперь мы будем использовать подключаемый модуль пользовательских шлюза в новый, пустой модуль, который мы только что создали.

### Создание plugin.service.ts

Перейдите в каталог новый модуль средства, созданного ранее (```\src\app\{!Module-Name}```) и создать новый файл ```plugin.service.ts```.

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

Измените ссылки на ```Sample Uno``` и ```Sample%20Uno``` ей имя функции соответствующим образом.

[!WARNING]
> Это рекомендуется, встроенные в ```this.appContextService.node``` используется для вызова любой API-Интерфейс, определенного в ваш подключаемый модуль шлюза пользовательских. Это позволит гарантировать, если учетные данные необходимы внутри вашего подключаемый модуль шлюза, что они будут обработаны надлежащим образом.

### Изменение module.ts

Откройте ```module.ts``` файл новый модуль, созданные ранее (т. е. ```{!Module-Name}.module.ts```):

Добавьте следующие операторы импорта:

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

### Изменение component.ts

Откройте ```component.ts``` файл новый модуль, созданные ранее (т. е. ```{!Module-Name}.component.ts```):

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

Измените конструктор и изменить или добавить следующие функции:

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

### Изменение component.html ###

Откройте ```component.html``` файл новый модуль, созданные ранее (т. е. ```{!Module-Name}.component.html```):

На HTML-файл добавьте следующее содержимое:
``` html
<button (click)="onClick()" >go</button>
{{ responseResult }}
```

## Создание и загрузка расширения

Теперь вы готовы [Создание и загрузка](..\develop-tool.md#build-and-side-load-your-extension) расширения в Windows Admin Center.
