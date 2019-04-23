---
title: Изменение поведения корневой навигации
description: Разработка решения расширения пакета SDK Windows Admin Center (Гонолулу проекта) - изменения поведения навигации корневого
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 08/07/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: 4a5cba228aa3a0afed99c0d853c3720a5b46f650
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59861735"
---
# <a name="modify-root-navigation-behavior-for-a-solution-extension"></a>Изменение поведения навигации корневой для расширения решения

>Область применения. Windows Admin Center, предварительная версия Windows Admin Center

В этом руководстве мы узнаете, как изменить поведение навигации корневой для вашего решения, чтобы их поведение списка другое подключение, а также как скрыть или отобразить список инструментов.

## <a name="modifying-root-navigation-behavior"></a>Изменение поведения навигации корневого

Откройте файл manifest.json в \src {корневым каталогом расширения} и найдите свойство «rootNavigationBehavior». Это свойство имеет два допустимых значения: «подключения» или «path». Поведение «подключения» подробно описана далее в документации.

### <a name="setting-path-as-a-rootnavigationbehavior"></a>Задание пути как rootNavigationBehavior

Установите для параметра ```rootNavigationBehavior``` для ```path```, а затем удалите ```requirements``` свойство и оставляет ```path``` свойство как пустую строку. Вы завершили минимальный требуемую конфигурацию, чтобы построить расширение решения. Сохраните файл и сборки gulp "->" gulp служат вам средства, а затем стороны загружает расширение в локальном расширения Windows Admin Center.

Массив допустимых точек входа манифеста выглядит следующим образом:
```
    "entryPoints": [
        {
          "entryPointType": "solution",
          "name": "main",
          "urlName": "testsln",
          "displayName": "resources:strings:displayName",
          "description": "resources:strings:description",
          "icon": "sme-icon:icon-win-powerShell",
          "path": "",
          "rootNavigationBehavior": "path"
        }
    ],
```

Средства, созданные с помощью этого типа структуры будет подключения не требуется для загрузки, но либо не иметь функцию подключения узла.

### <a name="setting-connections-as-a-rootnavigationbehavior"></a>Параметры подключения, как rootNavigationBehavior

При задании ```rootNavigationBehavior``` свойства ```connections```, вы указываете оболочки Windows Admin Center будет наблюдаться подключенный узел (всегда сервер какого-либо типа), он должен подключиться и проверьте состояние подключения. Таким образом существует 2 действия проверки подключения. (1) Windows Admin Center попытается попытайтесь войти на узел с помощью учетных данных (для установления удаленного сеанса PowerShell), и 2) он будет выполняться скрипт PowerShell, предоставленный для идентификации, если узел находится в состоянии, доступном для подключения.

Определение правильное решение с подключения будет выглядеть следующим образом:

``` json
        {
          "entryPointType": "solution",
          "name": "example",
          "urlName": "solutionexample",
          "displayName": "resources:strings:displayName",
          "description": "resources:strings:description",
          "icon": "sme-icon:icon-win-powerShell",
          "rootNavigationBehavior": "connections",
          "connections": {
            "header": "resources:strings:connectionsListHeader",
            "connectionTypes": [
                "msft.sme.connection-type.example"
                ]
            },
            "tools": {
                "enabled": false,
                "defaultTool": "solution"
            }
        },
```

Если rootNavigationBehavior имеет значение «подключения» необходимо создавать определения подключений в манифесте. Это включает в себя свойство «header» (будет использоваться для отображения в заголовке решения при его выборе в меню), массив connectionTypes (этот параметр указывает какие connectionTypes используются в решении. Подробнее об этом в документации по connectionProvider.).

## <a name="enabling-and-disabling-the-tools-menu"></a>Включение и отключение меню "Сервис" ##

Другое свойство, доступных в определении решения является свойство «инструменты». Это будет определяться, если отображается меню "Сервис", а также средства, которые будут загружены. Если этот параметр включен, Windows Admin Center будет отображаться слева меню "Сервис". С помощью defaultTool, это необходимо добавить точку входа средство в манифест для загрузки необходимых ресурсов. Значение «defaultTool» должно быть свойство «name» средства, как это определено в манифесте.
