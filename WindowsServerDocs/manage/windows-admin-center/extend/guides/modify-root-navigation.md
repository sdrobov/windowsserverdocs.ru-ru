---
title: Изменение поведения корневой навигации
description: Разработка расширения решения Windows Admin Center SDK (Project Хонолулу) — изменение поведения корневой навигации
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 08/07/2018
ms.localizationpriority: medium
ms.prod: windows-server
ms.openlocfilehash: 78c94f3ea13f54ac31f9de9dd60873b93eba2c17
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71385279"
---
# <a name="modify-root-navigation-behavior-for-a-solution-extension"></a>Изменение поведения корневой навигации для расширения решения

>Область применения. Windows Admin Center, ознакомительная версия Windows Admin Center

В этом пошаговом окне мы расскажем, как изменить поведение корневой навигации для решения, чтобы оно имело различное поведение списка подключений, а также скрыть или Показать список инструментов.

## <a name="modifying-root-navigation-behavior"></a>Изменение поведения корневой навигации

Откройте файл manifest. JSON в {root расширения} \срк и найдите свойство "Рутнавигатионбехавиор". Это свойство имеет два допустимых значения: "Connections" или "Path". Поведение "подключения" подробно описано далее в документации.

### <a name="setting-path-as-a-rootnavigationbehavior"></a>Задание пути в качестве Рутнавигатионбехавиор

Присвойте параметру ```rootNavigationBehavior``` значение ```path```, а затем удалите свойство ```requirements``` и оставьте свойство ```path``` как пустую строку. Вы выполнили минимальную требуемую конфигурацию для создания расширения решения. Сохраните файл, а gulp Build-> gulp — как средство, а затем загрузите расширение в локальное расширение центра администрирования Windows.

Допустимый массив EntryPoint манифеста выглядит следующим образом:
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

Средства, созданные с такой структурой, не требуют подключения к нагрузке, но не будут иметь функций подключения к узлу.

### <a name="setting-connections-as-a-rootnavigationbehavior"></a>Настройка соединений как Рутнавигатионбехавиор

Если для свойства ```rootNavigationBehavior``` задано значение ```connections```, вы указываете оболочке центра администрирования Windows, что будет подключенным узлом (всегда является сервером какого-то типа), к которому должен подключаться, и проверить состояние подключения. В этом случае необходимо выполнить два шага проверки подключения. 1) в центре администрирования Windows будет предпринята попытка войти в узел с вашими учетными данными (для установления удаленного сеанса PowerShell) и 2) будет выполнен сценарий PowerShell, который вы задаете, чтобы определить, находится ли узел в состоянии подключения.

Допустимое определение решения с соединениями будет выглядеть следующим образом:

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

Если для Рутнавигатионбехавиор задано значение "Connections", то необходимо создать определение Connections в манифесте. Сюда входит свойство "заголовок" (будет использоваться для вывода в заголовке решения, когда пользователь выбирает его из меню) — массив Коннектионтипес (в этом случае будут указаны Коннектионтипес, используемые в решении. Дополнительные сведения см. в документации по connectionProvider.)

## <a name="enabling-and-disabling-the-tools-menu"></a>Включение и отключение меню "Сервис" ##

Другим свойством, доступным в определении решения, является свойство Tools. Это определит, отображается ли меню Сервис, а также средство, которое будет загружено. Если этот параметр включен, центр администрирования Windows выводит меню инструментов слева. При использовании Дефаулттул необходимо добавить точку входа средства в манифест, чтобы загрузить соответствующие ресурсы. Значение "Дефаулттул" должно быть свойством "Name" инструмента, как оно определено в манифесте.
