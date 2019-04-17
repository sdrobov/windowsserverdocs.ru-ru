---
title: Разработка расширения средства
description: Разработка расширения средства Windows Admin Center SDK (проект Honolulu)
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 09/18/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: 2269a2ac2cabda6f8fdd829994f36e89d581bd23
ms.sourcegitcommit: f1edfc6525e09dd116b106293f9260123a94de0c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "9297009"
---
# Установите расширение полезных данных на управляемый узел

>Относится к: Windows Admin Center, ознакомительная версия Windows Admin Center

## Настройка
> [!NOTE]
> Для выполнения в этом руководстве, вы должны создаст 1.2.1904.02001 или более поздней версии. Чтобы проверить сборку номер откройте Windows Admin Center и нажмите кнопку со знаком вопроса в верхнем правом углу.

Если вы еще не сделали этого, создание [расширения средства](../develop-tool.md) для Windows Admin Center. После завершения этого сделать внимание на значения, используемые при создании расширения:
| Значение | Объяснение | Пример. |
| ----- | ----------- | ------- |
| ```{!Company Name}``` | Название компании (с пробелами) | ```Contoso``` |
| ```{!Tool Name}``` | Ваше средство имя (пробелы) | ```InstallOnNode``` |

В вашей папке расширения средства создания ```Node``` папки (```{!Tool Name}\Node```). Все, что помещается в этой папке будут скопированы к управляемому узлу при использовании этого API. Добавьте все файлы, необходимые для вашей. 

Также создать ```{!Tool Name}\Node\installNode.ps1``` сценария. Этот сценарий будет выполнен на управляемый узел, после все файлы копируются из ```{!Tool Name}\Node``` папку к управляемому узлу. Добавьте дополнительную логику для вашей. Пример ```{!Tool Name}\Node\installNode.ps1``` файла:

``` ps1
# Add logic for installing payload on managed node
echo 'Success'
```

> [!NOTE]
> ```{!Tool Name}\Node\installNode.ps1``` имеет определенное имя, будет искать API. Изменение имени этого файла приведет к ошибке.


## Интеграция с пользовательским Интерфейсом

Обновление ```\src\app\default.component.ts``` следующее:

``` ts
import { Component } from '@angular/core';
import { AppContextService } from '@microsoft/windows-admin-center-sdk/angular';
import { Observable } from 'rxjs';

@Component({
  selector: 'default-component',
  templateUrl: './default.component.html',
  styleUrls: ['./default.component.css']
})

export class DefaultComponent {
  constructor(private appContextService: AppContextService) { }

  public response: any;
  public loading = false;

  public installOnNode() {
    this.loading = true;
    this.post('{!Company Name}.{!Tool Name}', '1.0.0',
      this.appContextService.activeConnection.nodeName).subscribe(
        (response: any) => {
          console.log(response);
          this.response = response;
          this.loading = false;
        },
        (error) => {
          console.log(error);
          this.response = error;
          this.loading = false;
        }
      );
  }

  public post(id: string, version: string, targetNode: string): Observable<any> {
    return this.appContextService.node.post(targetNode,
      `features/extensions/${id}/versions/${version}/install`);
  }

}
```
Обновление заполнителями для значений, которые использовались при создании расширения:
``` ts
this.post('contoso.install-on-node', '1.0.0',
      this.appContextService.activeConnection.nodeName).subscribe(
        (response: any) => {
          console.log(response);
          this.response = response;
          this.loading = false;
        },
        (error) => {
          console.log(error);
          this.response = error;
          this.loading = false;
        }
      );
```

Также обновить ```\src\app\default.component.html``` для:
``` html
<button (click)="installOnNode()">Click to install</button>
<sme-loading-wheel *ngIf="loading" size="large"></sme-loading-wheel>
<p *ngIf="response">{{response}}</p>
```
И наконец ```\src\app\default.module.ts```:
``` ts
import { CommonModule } from '@angular/common';
import { NgModule } from '@angular/core';

import { LoadingWheelModule } from '@microsoft/windows-admin-center-sdk/angular';
import { DefaultComponent } from './default.component';
import { Routing } from './default.routing';

@NgModule({
  imports: [
    CommonModule,
    LoadingWheelModule,
    Routing
  ],
  declarations: [DefaultComponent]
})
export class DefaultModule { }

```

## Создание и установка пакета NuGet

Последний шаг создание пакет NuGet с файлами, которые мы добавили с последующей установкой этот пакет в Windows Admin Center.

Если вы не создали пакет расширения до ознакомления с руководством [Публикация расширений](../publish-extensions.md) . 
> [!IMPORTANT]
> В файле .nuspec для этого расширения, очень важно, ```<id>``` значение совпадает с именем вашего проекта ```manifest.json``` и ```<version>``` соответствует, что было добавлено к ```\src\app\default.component.ts```. Также добавьте запись в разделе ```<files>```: 

> ```<file src="Node\**\*.*" target="Node" />```.

``` xml
<?xml version="1.0" encoding="utf-8"?>
<package xmlns="http://schemas.microsoft.com/packaging/2011/08/nuspec.xsd">
  <metadata>
    <id>contoso.install-on-node</id>
    <version>1.0.0</version>
    <authors>Contoso</authors>
    <owners>Contoso</owners>
    <requireLicenseAcceptance>false</requireLicenseAcceptance>
    <projectUrl>https://msft-sme.myget.org/feed/windows-admin-center-feed/package/nuget/contoso.sme.install-on-node-extension</projectUrl>
    <licenseUrl>http://YourLicenseLink</licenseUrl>
    <iconUrl>http://YourLogoLink</iconUrl>
    <description>Install on node extension by Contoso</description>
    <copyright>(c) Contoso. All rights reserved.</copyright> 
  </metadata>
    <files>
    <file src="bundle\**\*.*" target="ux" />
    <file src="package\**\*.*" target="gateway" />
    <file src="Node\**\*.*" target="Node" />
  </files>
</package>
```

После создания этого пакета, добавьте путь к этой веб-канала. В Windows Admin Center перейдите > параметры > расширений веб-каналы и добавьте путь к там, где присутствует этот пакет. При расширении выполняется устанавливаемого, вы сможете щелкните ```install``` будут вызваны кнопки и API.  