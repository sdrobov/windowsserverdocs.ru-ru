---
title: Добавить модуль расширения средства
description: Разработка расширения средства Windows Admin Center SDK (проект Honolulu) — добавить модуль расширения средства
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 09/18/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: e6978ce20a7c6da8addb217de8d30f733b40d261
ms.sourcegitcommit: be0144eb59daf3269bebea93cb1c467d67e2d2f1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/20/2018
ms.locfileid: "4081211"
---
# Добавить модуль расширения средства

>Относится к: Windows Admin Center, ознакомительная версия Windows Admin Center

В этой статье мы добавим пустой модуль расширения средства, которые мы создали с помощью Windows Admin Center CLI.

## Подготовка среды

Если вы еще не сделали этого, следуйте инструкциям в разработке расширение [средства](..\develop-tool.md) (или [решение](..\develop-solution.md)) чтобы подготовить свою среду и создать новый, пустой средство расширение.

## Используйте Angular CLI, чтобы создать модуль (и компонент)

Если вы не знакомы с Angular, настоятельно рекомендуется прочитать документацию на веб-сайте Angular.Io, чтобы ознакомиться с Angular и NgModule. Дополнительные сведения о NgModule см. здесь: https://angular.io/guide/ngmodule

* Дополнительные сведения о создании нового модуля в Angular CLI: https://github.com/angular/angular-cli/wiki/generate-module
* Дополнительные сведения о создании нового компонента в Angular CLI: https://github.com/angular/angular-cli/wiki/generate-component


Откройте командную строку, измените каталог на \src\app в свой проект, а затем выполните следующие команды, заменив ```{!ModuleName}``` именем своего модуля (пробелы удалены):

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


## Добавление сведений о маршрутизации

Если вы не знакомы с Angular, настоятельно рекомендуется ознакомиться с маршрутизацией и навигацией в Angular. В следующих разделах рассматриваются необходимые элементы маршрутизации, которые позволяют Windows Admin Center переходить к вашему расширению и между представлениями в вашем расширении в ответ на действия пользователя. Подробнее см. здесь: https://angular.io/guide/router

Используйте то же имя модуля, которое вы использовали на предыдущем этапе.

### Добавление содержимого в новый файл маршрутизации

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

### Добавление содержимого в новый файл модуля

Откройте файл ```{!module-name}.module.ts```, соответствующий этому соглашению об именовании:

| Значение | Объяснение | Пример имени файла |
| ----- | ----------- | ------- |
| ```{!module-name}``` | Имя модуля (нижний регистр, пробелы заменены на тире) | ```manage-foo-works-portal.module.ts``` |

* Добавьте содержимое в файл:

    ``` ts
    import { Routing } from './{!module-name}.routing';
    ```

* Замените значения в только что созданном содержимом необходимыми значениями:

    | Значение | Объяснение | Пример. |
    | ----- | ----------- | ------- |
    | ```{!module-name}``` | Имя модуля (нижний регистр, пробелы заменены на тире) | ```manage-foo-works-portal``` |

* Измените оператор imports, чтобы выполнить импорт маршрутизации:

    | Исходное значение | Новое значение |
    | -------------- | --------- |
    | ```imports: [ CommonModule ]``` | ```imports: [ CommonModule, Routing ]``` |

* Убедитесь, что операторы ```import``` упорядочены в алфавитном порядке по источнику.

### Добавление содержимого в новый файл компонента typescript

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
### Обновление приложения routing.module.ts

Откройте файл ```app-routing.module.ts```и изменить путь по умолчанию, поэтому он загрузит новый модуль, который вы только что создали.  Найдите запись для ```path: ''```и обновите ```loadChildren``` для загрузки модуля вместо модуль по умолчанию:

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
Ниже приведен пример пути по умолчанию обновлена.
``` ts
    {
        path: '', 
        loadChildren: 'app/manage-foo-works-portal/manage-foo-works-portal.module#ManageFooWorksPortalModule'
    },
```


## Создание и загрузка расширения

Теперь вы добавили модуля для расширения.  Затем вы можете [Создание и загрузка](..\develop-tool.md#build-and-side-load-your-extension) расширения в Windows Admin Center, чтобы увидеть результат.
