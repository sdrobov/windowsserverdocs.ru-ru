---
title: Разработка расширения решения
description: Разработка расширения решения Windows Admin Center SDK (проект Honolulu)
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 09/18/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: ed5ecddbaef91f127846825e408a9a6ec65ff741
ms.sourcegitcommit: be0144eb59daf3269bebea93cb1c467d67e2d2f1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/20/2018
ms.locfileid: "4081071"
---
# Разработка расширения решения

>Относится к: Windows Admin Center, ознакомительная версия Windows Admin Center

Решения, в основном, определяют уникальный тип объекта, с которым вы хотите управлять через Windows Admin Center.  Эти типы решений или подключения входят в состав Windows Admin Center по умолчанию:

* Подключения Windows Server
* Подключения ПК с Windows
* Подключения отказоустойчивого кластера
* Гиперконвергентные кластера

При выборе подключения на странице подключения Windows Admin Center загружается расширение решения для такого подключения типа, а Windows Admin Center будет пытаться подключиться к целевому узлу. Если подключение выполнено успешно, решение будет загружаться расширения пользовательского интерфейса, и Windows Admin Center будет отображать средства для этого решения в левой области навигации.

Если вы хотите построить управления графический интерфейс пользователя для службы, не определенные типы подключений по умолчанию выше, например сетевой коммутатор или другому оборудованию невидимым по имени компьютера, может потребоваться создать собственный расширения решения.

> [!NOTE]
> Не знакомы с типами другое расширение? Дополнительные сведения о [расширяемости типы архитектуры и расширение](understand-extensions.md).

## Подготовка среды

Если вы еще не сделали этого, [Подготовьте свою среду](prepare-development-environment.md) , установив зависимостей и глобального компонентов, необходимых для всех проектов.

## Создание нового расширения решения с помощью Windows Admin Center CLI ##

Получив все зависимости, которые устанавливаются, вы готовы создать новое расширение решения.  Создание или перейдите к папке, содержащей файлы проекта, откройте командную строку и задать эту папку в качестве рабочий каталог.  С помощью CLI центра администрирования Windows, который ранее был установлен, создайте новое расширение с помощью следующего синтаксиса:

```
wac create --company "{!Company Name}" --solution "{!Solution Name}" --tool "{!Tool Name}"
```

| Значение | Объяснение | Пример. |
| ----- | ----------- | ------- |
| ```{!Company Name}``` | Название компании (с пробелами) | ```Contoso Inc``` |
| ```{!Solution Name}``` | Имя вашего решения (с пробелами) | ```Contoso Foo Works Suite``` |
| ```{!Tool Name}``` | Ваше средство имя (пробелы) | ```Manage Foo Works``` |

Вот пример использования:

```
wac create --company "Contoso Inc" --solution "Contoso Foo Works Suite" --tool "Manage Foo Works"
```

В результате создается новая папка в текущий рабочий каталог с именем, заданным для решения, копирует все необходимые шаблона файлы в свой проект и настраивает файлы с вашей компании, решения и имя инструмента.  

Затем измените каталог в папке только что создали, а затем установите необходимые локальные зависимости, выполнив следующую команду:

```
npm install
```

По завершении этого настройки все необходимые для загрузки нового расширения в Windows Admin Center. 

## Добавление содержимого в расширении

Теперь, когда вы создали расширения с помощью Windows Admin Center CLI, все готово для настройки содержимого.  См. следующие руководства по примеры того, вы можете:

- Добавление [пустой модуль](guides\add-module.md)
- Добавьте [Интернет-кадра](guides\add-iframe.md)
- Создание [поставщика пользовательские подключения](guides\create-connection-provider.md)
- [Корневой](guides\modify-root-navigation.md) поведения навигации
 
Даже Дополнительные примеры можно найти нашем [сайте GitHub SDK](https://aka.ms/wacsdk):
-  [Средства разработчика](https://github.com/Microsoft/windows-admin-center-sdk/tree/master/windows-admin-center-developer-tools) — это полнофункциональное расширение, которое может быть неопубликованным в Windows Admin Center и содержит широкий набор пример функциональных возможностей и примеры средства, которые можно просматривать и использовать в собственном расширении.

## Создание и загрузка расширения

Затем создание и загрузка расширения в Windows Admin Center.  Откройте окно командной строки, измените каталог на каталог источника, а затем все готово для построения.

* Создание и обслуживание с помощью Gulp:

    ```
    gulp build
    gulp serve -p 4201
    ```

Обратите внимание, что необходимо выбрать порт, который в данный момент будет не занят. Убедитесь, что вы не используете порт, на котором работает Windows Admin Center.

Проект можно загрузить в локальный экземпляр Windows Admin Center для тестирования, присоединив локально обслуживаемый проект к Windows Admin Center.

* Запустите Windows Admin Center в веб-браузере
* Откройте отладчик (F12)
* Откройте консоль и введите следующую команду:

    ```
    MsftSme.sideLoad("http://localhost:4201")
    ```

*   Обновите веб-браузер

Теперь проект будет отображаться в списке "Средства" (неопубликованный) рядом с соответствующим именем.

## Выбрать другую версию пакета SDK Windows Admin Center

Поддержание в актуальном состоянии с помощью пакета SDK изменений и платформы расширения очень просто.  Прочитать о том, как [другая версия целевого](target-sdk-version.md) пакета SDK Windows Admin Center.