---
title: Добавление модуля в расширение средства
description: Разработка расширение средства пакета SDK Windows Admin Center (Гонолулу проекта) — Добавление модуля к расширению средства
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 09/18/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: e6978ce20a7c6da8addb217de8d30f733b40d261
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59834405"
---
# <a name="add-a-module-to-a-tool-extension"></a>Добавление модуля в расширение средства

>Область применения. Windows Admin Center, предварительная версия Windows Admin Center

В этой статье мы добавим пустой модуль расширения инструмент, который мы создали с помощью интерфейса командной строки Windows Admin Center.

## <a name="prepare-your-environment"></a>Подготовка среды

Если это еще не сделано, следуйте указаниям, приведенным в разработке [средство](..\develop-tool.md) (или [решение](..\develop-solution.md)) расширение для подготовки среды и создать новый, пустой средство расширение.

## <a name="use-the-angular-cli-to-create-a-module-and-component"></a>С помощью Angular CLI для создания модуля (и компонент)

Если вы не знакомы с Angular, настоятельно рекомендуется прочитать документацию на веб-сайте Angular.Io, чтобы ознакомиться с Angular и NgModule. Дополнительные сведения о NgModule см. здесь: https://angular.io/guide/ngmodule

* Дополнительные сведения о создании нового модуля в Angular CLI: https://github.com/angular/angular-cli/wiki/generate-module
* Дополнительные сведения о создании нового компонента в Angular CLI: https://github.com/angular/angular-cli/wiki/generate-component


Откройте командную строку, измените каталог \src\app в проекте, а затем выполните следующие команды, заменив ```{!ModuleName}``` именем своего модуля (с пробелами):

```
cd \src\app
ng generate module {!ModuleName}
ng generate component {!ModuleName}
```

| Значение | Объяснение | Пример |
| ----- | ----------- | ------- |
| ```{!ModuleName}``` | Имя модуля (пробелы удалены) | ```ManageFooWorksPortal``` |

Пример использования:
```
cd \src\app
ng generate module ManageFooWorksPortal
ng generate component ManageFooWorksPortal
```


## <a name="add-routing-information"></a>Добавление сведений о маршрутизации

Если вы не знакомы с Angular, настоятельно рекомендуется ознакомиться с маршрутизацией и навигацией в Angular. В следующих разделах рассматриваются необходимые элементы маршрутизации, которые позволяют Windows Admin Center переходить к вашему расширению и между представлениями в вашем расширении в ответ на действия пользователя. Подробнее см. здесь: https://angular.io/guide/router

Используйте имя модуля, которое вы использовали на предыдущем шаге.

### <a name="add-content-to-new-routing-file"></a>Добавление содержимого в новый файл маршрутизации

* Перейдите к папке модуля, созданной с помощью ``` ng generate ``` на предыдущем шаге.

* Создайте новый файл ```{!module-name}.routing.ts```, следуя этому соглашению об именовании:

    | Значение | Объяснение | Пример имени файла |
    | ----- | ----------- | ------- |
    | ```{!module-name}``` | Имя модуля (нижний регистр, пробелы заменены на тире) | ```manage-foo-works-portal.routing.ts``` |

* Добавьте это содержимое в только что созданный файл:

    ``` ts
    import { NgModule } from '@angular/core';
    import { RouterModule, Routes } from '@angular/router';
    import { {!ModuleName}Component } from './{!module-name}.component';

    const routes: Routes = [
        {
            path: '',
            component: {!ModuleName}Component,
            // if the component has child components that need to be routed to, include them in the children array.
            children: [
                {
                    path: '', 
                    redirectTo: 'base',
                    pathMatch: 'full'
                }
            ]
    }];

    @NgModule({
        imports: [
            RouterModule.forChild(routes)
        ],
        exports: [
            RouterModule
        ]
    })
    export class Routing { }
    ```

* Замените значения в только что созданном файле необходимыми значениями:

    | Значение | Объяснение | Пример |
    | ----- | ----------- | ------- |
    | ```{!ModuleName}``` | Имя модуля (пробелы удалены) | ```ManageFooWorksPortal``` |
    | ```{!module-name}``` | Имя модуля (нижний регистр, пробелы заменены на тире) | ```manage-foo-works-portal``` |

### <a name="add-content-to-new-module-file"></a>Добавление содержимого в новый файл модуля

Откройте файл ```{!module-name}.module.ts```, соответствующий этому соглашению об именовании:

| Значение | Объяснение | Пример имени файла |
| ----- | ----------- | ------- |
| ```{!module-name}``` | Имя модуля (нижний регистр, пробелы заменены на тире) | ```manage-foo-works-portal.module.ts``` |

* Добавьте содержимое в файл:

    ``` ts
    import { Routing } from './{!module-name}.routing';
    ```

* Замените значения в только что созданном содержимом необходимыми значениями:

    | Значение | Объяснение | Пример |
    | ----- | ----------- | ------- |
    | ```{!module-name}``` | Имя модуля (нижний регистр, пробелы заменены на тире) | ```manage-foo-works-portal``` |

* Измените оператор imports, чтобы выполнить импорт маршрутизации:

    | Исходное значение | Новое значение |
    | -------------- | --------- |
    | ```imports: [ CommonModule ]``` | ```imports: [ CommonModule, Routing ]``` |

* Убедитесь, что операторы ```import``` упорядочены в алфавитном порядке по источнику.

### <a name="add-content-to-new-component-typescript-file"></a>Добавьте новый файл компонента typescript содержимое

Откройте файл ```{!module-name}.component.ts```, соответствующий этому соглашению об именовании:

| Значение | Объяснение | Пример имени файла |
| ----- | ----------- | ------- |
| ```{!module-name}``` | Имя модуля (нижний регистр, пробелы заменены на тире) | ```manage-foo-works-portal.component.ts``` |
    
Измените содержимое в файле на следующее:

``` ts
constructor() {
    // TODO
}

public ngOnInit() {
    // TODO
}
```
### <a name="update-app-routingmodulets"></a>Обновление приложения routing.module.ts

Открыть файл ```app-routing.module.ts```и измените путь по умолчанию, чтобы он загрузит новый модуль, который вы только что создали.  Найти запись для ```path: ''```и обновите ```loadChildren``` загрузить модуль вместо модуль по умолчанию:

| Значение | Объяснение | Пример |
| ----- | ----------- | ------- |
| ```{!ModuleName}``` | Имя модуля (пробелы удалены) | ```ManageFooWorksPortal``` |
| ```{!module-name}``` | Имя модуля (нижний регистр, пробелы заменены на тире) | ```manage-foo-works-portal``` |

``` ts
    {
        path: '', 
        loadChildren: 'app/{!module-name}/{!module-name}.module#{!ModuleName}Module'
    },
```
Вот пример пути по умолчанию обновлен:
``` ts
    {
        path: '', 
        loadChildren: 'app/manage-foo-works-portal/manage-foo-works-portal.module#ManageFooWorksPortalModule'
    },
```


## <a name="build-and-side-load-your-extension"></a>Сборки и на стороне загрузить расширение

Теперь вы добавили модуля для расширения.  Далее можно [построения и стороны нагрузки](..\develop-tool.md#build-and-side-load-your-extension) расширения в Windows Admin Center, чтобы просмотреть результаты.
