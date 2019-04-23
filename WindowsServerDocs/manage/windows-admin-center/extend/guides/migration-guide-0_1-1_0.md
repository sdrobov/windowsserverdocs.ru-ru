---
title: Перенос из пакета SDK для Windows Admin Center 0,1 до 1,0
description: Это руководство поможет вам перенести из пакета SDK Windows Admin Center версии 0,1 до 1,0
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 02/26/2019
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: ba0e8cda35c51763b5c10b89c76e2bf07e064dfd
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59886475"
---
# <a name="migrate-from-windows-admin-center-sdk-01-to-10"></a>Перенос из пакета SDK для Windows Admin Center 0,1 до 1,0

>Область применения. Ознакомительная версия Windows Admin Center

Это руководство поможет вам перенести из пакета SDK Windows Admin Center версии 0,1 до 1,0.  

## <a name="1-learn-about-new-controls-with-the-dev-guide-extension"></a>1. Дополнительные сведения о новых элементов управления с расширением Dev Guide

Windows Admin Center 1902 и более поздних версий включает в себя **Dev Guide** расширение, которое можно использовать, чтобы найти примеры элементов управления (включая новые элементы управления) и сценариев, помогающие вам создавать собственное расширение.  Руководство по разработке заменяет **средств разработчика** расширения из более ранних версиях пакета SDK.

### <a name="use-the-dev-guide-in-windows-admin-center"></a>Воспользуйтесь руководством по разработке в Windows Admin Center

Руководство по разработке доступны как решение в версии Windows Admin Center 1902 и более поздние версии.  Руководство по разработке предварительно установлен, но его необходимо включить с помощью параметров.

**Включите руководство по разработке в Windows Admin Center:**

* Открыть Windows Admin Center (версия 1902 и более поздние версии)
* Щелкните **параметры** значок в правом верхнем углу окна
* Выберите **Дополнительно** вкладку
* В разделе *эксперимента ключи*, нажмите кнопку **добавить**
* Введите новое значение ```msft.sme.shell.devguide``` в пустое поле, созданный на предыдущем шаге
* Нажмите кнопку **сохранен и перезагружен**

**Откройте руководство по разработке в Windows Admin Center:**

* Открыть Windows Admin Center (версия 1902 и более поздние версии)
* Нажмите кнопку раскрывающегося списка в верхнем левом углу, чтобы показать все типы решений
* Выберите **Dev Guide** решения 
    * Если вы не видите решения в списке, убедитесь, что вы включили в руководстве по разработки (см. раздел выше) и Windows Admin Center, загружаются в память.
* Обзор содержимое руководства разработки, выбрав одну из вкладок
    * **Целевая:** Содержит примеры кода для *Manage As* и *уведомления* сценариев
    * **Элементы управления.** Примеры элементов управления, доступных в пакете SDK
    * **Каналы:** Содержит примеры прогнозируемых доступные функции преобразователя и модуля форматирования
    * **Стили:** Содержит примеры стилей CSS, доступных в пакете SDK
    * **MsftSme:** Содержит примеры и руководства для более сложных сценариев 

### <a name="browse-the-source-code-of-dev-guide-on-github"></a>Просмотреть исходный код руководства разработчиков на сайте GitHub

Вы можете просмотреть [исходный код](https://github.com/Microsoft/windows-admin-center-sdk/) руководства разработки на GitHub, чтобы найти пример примеры кода HTML, CSS и TypeScript.

## <a name="2-prepare-your-development-environment-for-the-latest-sdk"></a>2. Подготовка среды разработки для последнего пакета SDK

Установить или обновить версию node.js [10.15.1 LTS или более поздней версии](https://nodejs.org/en/).

Интерфейс командной строки Windows Admin Center обновите до последней версии:

[//]: # "npm удалить -g windows-admin-center-cli@next"

``` cmd
npm uninstall -g windows-admin-center-cli
npm install -g windows-admin-center-cli
```

Обновление глобальных зависимости для этих версий:

``` cmd
npm install npm@6.4.1 -g
npm install @angular/cli@7.1.2 -g
npm install gulp -g
npm install typescript@3.1.6 -g
npm install tslint@5.11.0 -g
```

## <a name="3-create-a-new-project-with-the-latest-sdk"></a>3. Создайте новый проект с помощью последнего пакета SDK

Создайте новый проект для платформы с помощью CLI Windows Admin Center ```next``` версии (пакет SDK 1.0):

[//]: # "WAC create--компании «Contoso Inc»--средство «Управление Foo Works'--экспериментальной версии"

``` cmd
wac create --company "Contoso Inc" --tool "Manage Foo Works" --version next
```

Затем перейдите в папку, в только что создали, а затем установите необходимые зависимости для локального, выполнив ```npm install ```.

## <a name="4-modify-an-existing-project-to-use-the-latest-sdk"></a>4. Изменить существующий проект для использования последнего пакета SDK

ВНИМАНИЕ! Создайте резервную копию проекта перед продолжением.

Измените следующую строку в ```package.json``` к целевому объекту ```next``` версии (пакет SDK 1.0):

[//]: # ""@microsoft/windows-admin-center-sdk": «экспериментальный»"

``` json
"@microsoft/windows-admin-center-sdk": "next",
```

Затем запустите ```npm install``` для обновления ссылок во всем проекте.

## <a name="5-use-the-sdk-cli-to-fix-common-migration-issues"></a>5. Использование интерфейса командной строки пакета SDK для устранения распространенных проблем миграции

ВНИМАНИЕ! Создайте резервную копию проекта перед продолжением.

Из корневой папки проекта выполните следующую команду интерфейса командной строки на проект, чтобы автоматически исправлять распространенные проблемы миграции:

``` cmd
wac updateSeven --update
```

Эта команда интерфейса командной строки автоматически решает следующие проблемы:

* Повторное создание ```package-lock.json```
* Обновление файлов в среде angular компиляции:
    - ```.gitignore```
    - ```tslint.json```
    - ```tsconfig.json```
    - ```tsconfig.inline.json```
    - ```ng-package.json```
    - ```angular.json```
    - ```src\tsconfig.app.json```
    - ```src\tsconfig.lib.json```
    - ```src\tsconfig.spec.json```

## <a name="6-use-the-sdk-cli-to-understand-common-migration-issues"></a>6. С помощью интерфейса командной строки пакета SDK можно определить общие вопросы

Из корневой папки проекта, выполните следующую команду интерфейса командной строки для аудита проекта и выявить распространенные проблемы миграции, которые должны быть исправлены вручную:

``` cmd
wac updateSeven --audit
```

Это будет найти экземпляры следующих проблем в проекте:

### <a name="replace-usage-of-the-following-css-classes-with-these-sme-classes"></a>Замените эти классы специалист-эксперт использование следующих классов CSS:

| Старый класс CSS | Новый класс CSS |
| -- | -- |
| .auto-flex-size |  .sme-position-flex-auto |
| .Border-all |  .sme границы отступ sm и .sme-border-color-base-90 |
| .Border сверху вниз |  .sme границы нижней sm и .sme-border-bottom-color-base-90 |
| горизонтальный .border |  .sme границы горизонтальный sm и .sme-border-horizontal-color-base-90 |
| левый .border |  .sme-border-left-sm и .sme-border-left-color-base-90 |
| правый .border |  .sme-border справа sm и .sme-border-right-color-base-90 |
| .Border-top |  .sme-border-top-sm и .sme-border-top-color-base-90 |
| по вертикали .border |  .sme-border-vertical-sm и .sme-border-vertical-color-base-90 |
| .break-word |  .sme-arrange-ws-wrap |
| .btn |  .sme кнопку или кнопку |
| основной .btn |  .button.sme OR .sme-button.sme кнопка primary-кнопка — основной |
| темный .color |  .sme-color-alt |
| .Color света |  .sme-color-base |
| .Color светло серый |  .sme-color-base-90 |
| .fixed-flex-size |  .sme-position-flex-none |
| .flex-layout |  .sme упорядочить stack-h или .sme упорядочить stack-v |
| .font-bold |  .sme-font-emphasis1 |
| .Highlight |  .sme фона--желтый цвет |
| .Horizontal |  .sme упорядочить stack-h |
| не проверяются прокрутки |  .sme-position-flex-auto |
| .nowrap |  .sme упорядочить stack-h или .sme упорядочить stack-v |
| .Relative |  Отсчитываемый с .sme макета |
| .relative-center |  .sme макета абсолютного .sme расположение — по центру |
| .Reverse |  .sme упорядочить stack-в обратном порядке |
| .stretch-absolute |  .sme макета абсолютного .sme позиции отступ — none |
| .stretch-fixed |  исправлена .sme макета .sme позиции отступ — none |
| по вертикали .stretch |  .sme позиции stretch-v |
| .stretch-width |  .sme позиции stretch-h |
| .Vertical |  .sme упорядочить stack-v |
| только .vertical прокрутки |  .sme-arrange-overflow-hide-x sme-arrange-overflow-auto-y |
| .wrap |  .sme упорядочить wrapstack-h или .sme упорядочить wrapstack-v |

### <a name="replace-usage-of-the-following-components-with-these-sme-components"></a>Замените эти компоненты специалист-эксперт использование следующих компонентов:

| Старый компонент | Новый компонент |
| -- | -- |
| .Alert |  специалист-эксперт предупреждение |
| опасность .alert |  специалист-эксперт предупреждение |
| .breadCrumb |  специалист-эксперт предупреждение |
| .CheckBox |  sme-form-field[type="checkbox"] |
| .ComboBox |  sme-form-field[type="select"] |
| .Dashboard |  специалист-эксперт макета содержимое зоны дополняются специалист-эксперт — упорядочить stack-h |
| панель .details |  специалист-эксперт сетки свойств |
| .Details контейнера panel |  специалист-эксперт сетки свойств |
| .Details вкладка |  специалист-эксперт сетки свойств или специалистами-экспертами pivot |
| .Details оболочки |  специалист-эксперт сетки свойств |
| .disabled |  специалист-эксперт отключено |
| .Form кнопки | специалист-эксперт поля формы |
| .form-control | специалист-эксперт поля формы |
| .form-controls | специалист-эксперт поля формы |
| .Form группы | специалист-эксперт поля формы |
| Метка .form группы | специалист-эксперт поля формы |
| входные данные .form | специалист-эксперт поля формы |
| .Form stretch | специалист-эксперт поля формы |
| .Input файл | специалист-эксперт поля формы |
| .nav-tabs |  специалист-эксперт pivot |
| .Radio |  sme-form-field[type="radio"] |
| ֺכ .required | специалист-эксперт поля формы |
| .searchbox |  sme-form-field[type="search"] |
| .Toggle коммутатор |  sme-form-field[type="toggle-switch"] |
| содержащих контейнера |  специалист-эксперт макета содержимое зон и специалист-эксперт макета содержимое зоны дополняются |

### <a name="these-css-classes-are-deprecated-and-are-no-longer-supported"></a>Эти классы CSS устарели и больше не поддерживаются:

| Старый класс | Не рекомендуется |
| -- | -- |
| .acceptable | (устарело) |
| .color-error | (устарело) |
| .Color-info | (устарело) |
| .color-success | (устарело) |
| Предупреждение .color | (устарело) |
| .DELETE кнопка | (устарело) |
| .details-content | (устарело) |
| .Error покрытия | (устарело) |
| .Error сообщение | (устарело) |
| кнопка .guided области | (устарело) |
| .header-container | (устарело) |
| .icon win | (устарело) |
| .Indent | (устарело) |
| .Invalid | (устарело) |
| .Item-list | (устарело) |
| прокручиваемые .modal | (устарело) |
| . несколькими раздел | (устарело) |
| .no-action-bar | (устарело) |
| .Overflow поля | (устарело) |
| .Overflow средство | (устарело) |
| .Progress покрытия | (устарело) |
| Вот панель | (устарело) |
| .ROLLUP | (устарело) |
| .ROLLUP-status | (устарело) |
| .ROLLUP заголовок | (устарело) |
| значение .rollup | (устарело) |
| .searchbox-action-bar | (устарело) |
| .Size-h-1 | (устарело) |
| .Size-h-2 | (устарело) |
| .Size-h-3 | (устарело) |
| .Size-h-4 | (устарело) |
| .Size-h-full | (устарело) |
| .Size-h половину | (устарело) |
| .Size-v-1 | (устарело) |
| .Size-v-2 | (устарело) |
| .Size-v-3 | (устарело) |
| .Size-v-4 | (устарело) |
| .status-icon | (устарело) |
| .svg-16px | (устарело) |
| .Table отступа | (устарело) |
| .Table sm | (устарело) |
| .Thin | (устарело) |
| .Tile | (устарело) |
| .Tile текст | (устарело) |
| .Tile-content | (устарело) |
| нижний колонтитул .tile | (устарело) |
| .Tile заголовок | (устарело) |
| .Tile макета | (устарело) |
| Таблица .tile | (устарело) |
| .ToolBar | (устарело) |
| содержащих и нечетных строк | (устарело) |
| содержащих заголовок | (устарело) |
| содержащих заголовок box | (устарело) |
| содержащих области | (устарело) |
| .Usage и нечетных строк | (устарело) |
| области .usage строки | (устарело) |
| .Usage фона панели | (устарело) |
| .Usage заголовок панели | (устарело) |
| значение для столбца .usage | (устарело) |
| .Usage диаграммы | (устарело) |
| .Usage сообщение | (устарело) |
| область .usage сообщений | (устарело) |
| Заголовок .usage сообщения | (устарело) |
| .Warning | (устарело) |
| .white-space | (устарело) |

## <a name="7-understand-and-resolve-issues-with-observable-objects"></a>7. Понимание и устранение проблем с отслеживаемыми объектами

### <a name="update--rxjs-function-use-for-observable-objects"></a>Обновление ```rxjs``` функции наблюдаемые объекты

Ниже приведены некоторые общие имена функций, которые были изменены, могут существовать другие в проекте.

* Обновление ```Observable.empty()``` для ```empty()```
* Обновление ```Observable.of()``` для ```of()```
* Обновление ```.switchMap()``` для ```.pipe(switchMap())```
* Обновление ```.map()``` для ```.pipe(map())```
* Обновление ```flatMap()``` для ```mergeMap()```


### <a name="resolve-runtime-issues-with-map-and-filter-functions-on-observable-objects"></a>Устранение проблем среды выполнения с ```.map()``` и ```.filter()``` функций для наблюдаемых объектов

Если компилятор не может правильно идентифицировать ```observable``` тип объекта, ```.map()``` и ```.filter()``` функции ```array``` объекта могут быть связаны с вместо объекта, приводит к ошибкам во время выполнения.  Убедитесь, что ваши функции возвращают ```observable``` объекта, указав явный тип данных во избежание этой проблемы.

```any``` и без возвращаемого типа может вызвать эту проблему, найдите код с этими шаблонами:

``` ts
public getMyObservable(): any { //any return type can cause issues
 ...
}

public getMyObservable() { //no return type can cause issues
...
}
```

## <a name="8-resolve-other-common-issues"></a>8. Устраните другие распространенные проблемы

Эти методики помогут устранить другие типичные проблемы:

* Запустите ```ng lint --fix``` для устранения распространенных проблем lint
* Запустите ```gulp build``` многократно чтобы постепенно устранить неполадки, ```gulp build``` может автоматически разрешать

## <a name="9-build-and-serve-your-project"></a>9. Сборку и будут обслуживать проекта

Выполните следующие команды, чтобы создавать и обслуживать проекта до последней версии (пакет SDK 1.0).

``` cmd
gulp build
gulp serve --port 4201
```

## <a name="10-turn-on-dark-theme-in-windows-admin-center"></a>10. Включить Windows Admin Center "темной" теме

Чтобы включить темной темой в Windows Admin Center версии 1902 и более поздние версии, выполните следующие действия.

* Открыть Windows Admin Center (версия 1902 и более поздние версии)
* Щелкните **параметры** значок в правом верхнем углу окна
* Выберите **Дополнительно** вкладку
* В разделе *эксперимента ключи*, нажмите кнопку **добавить**
* Введите новое значение ```msft.sme.shell.personalization``` в пустое поле, созданный на предыдущем шаге
* Нажмите кнопку **сохранен и перезагружен**
* Параметры получают новую вкладку, **персонализации**.  Выберите на этой вкладке
* Изменение **цвета** для **темно-режим (Предварительная версия)**
