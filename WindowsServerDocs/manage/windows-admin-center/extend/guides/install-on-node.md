---
title: Разработка расширения средства
description: Разработка модуля средства пакета SDK Windows Admin Center (Гонолулу проекта)
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 09/18/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: 1a068c0d33887e8e9287ff15c1aa14f3dc84915a
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66445930"
---
# <a name="install-extension-payload-on-a-managed-node"></a>Установка расширения полезных данных на управляемом узле

>Область применения. Windows Admin Center, предварительная версия Windows Admin Center

## <a name="setup"></a>Установка
> [!NOTE]
> Для следуйте этому руководству, вы должны построим 1.2.1904.02001 или более поздней версии. Чтобы проверить сборку номер откройте Windows Admin Center и щелкните вопросительный знак в правом верхнем углу.

Если это еще не сделано, создайте [средство расширения](../develop-tool.md) для Windows Admin Center. После завершения этого сделать Обратите внимание на значения, используемые при создании расширения:

| Значение | Объяснение | Пример |
| ----- | ----------- | ------- |
| ```{!Company Name}``` | Название организации (с пробелами) | ```Contoso``` |
| ```{!Tool Name}``` | Имя инструмента (с пробелами) | ```InstallOnNode``` |

В папке средства расширения создайте ```Node``` папку (```{!Tool Name}\Node```). Все, что помещено в этой папке будут скопированы на управляемый узел при использовании этого API. Добавьте все файлы, необходимые для вашего варианта использования. 

Также создайте ```{!Tool Name}\Node\installNode.ps1``` скрипта. Этот сценарий будет выполняться на управляемом узле, как только все файлы копируются из ```{!Tool Name}\Node``` папки на управляемый узел. Добавьте дополнительную логику для варианта использования. Пример ```{!Tool Name}\Node\installNode.ps1``` файла:

``` ps1
# Add logic for installing payload on managed node
echo 'Success'
```

> [!NOTE]
> ```{!Tool Name}\Node\installNode.ps1``` имеет определенное имя для поиска API. Изменение имени этого файла приведет к ошибке.


## <a name="integration-with-ui"></a>Интеграция с пользовательским Интерфейсом

Обновление ```\src\app\default.component.ts``` следующим:

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
Обновите заполнители для значений, которые использовались при создании расширения:
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
И, наконец ```\src\app\default.module.ts```:
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

## <a name="creating-and-installing-a-nuget-package"></a>Создание и установка пакета NuGet

Последний шаг создания пакета NuGet с файлами, которые мы добавили и затем установке этого пакета в Windows Admin Center.

Выполните [публикации расширения](../publish-extensions.md) руководство, если вы не создали пакет расширения до. 
> [!IMPORTANT]
> В файле по файлу nuspec для данного расширения, очень важно, ```<id>``` значение совпадает с именем в проекте ```manifest.json``` и ```<version>``` соответствует, что был добавлен ```\src\app\default.component.ts```. Также добавьте запись в разделе ```<files>```: 
> 
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

После создания этого пакета, добавьте путь к этой веб-канала. В Windows Admin Center перейдите к параметрам > расширения > веб-каналов и добавьте путь к которой существует этот пакет. После завершения расширения в процессе установки можно нажать кнопку ```install``` кнопку и API будет вызываться.  