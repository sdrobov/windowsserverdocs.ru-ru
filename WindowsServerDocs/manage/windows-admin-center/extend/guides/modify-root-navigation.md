---
title: Изменение поведения корневой навигации
description: Разработка расширения решения Windows Admin Center SDK (проект Honolulu) - поведения навигации в корневой
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 08/07/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: 4a5cba228aa3a0afed99c0d853c3720a5b46f650
ms.sourcegitcommit: 546229d6b5fa7e16f725c6c35f4dcc272711b811
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2018
ms.locfileid: "4905044"
---
# Корневой поведения навигации для расширения решения

>Относится к: Windows Admin Center, ознакомительная версия Windows Admin Center

В этом руководстве мы узнаете, как изменить поведение навигации по корневой вести список другое соединение решения, а также как отображение или скрытие списка средств.

## Изменение поведения навигации в корневой

Откройте файл manifest.json в \src {расширение корень} и найдите свойство «rootNavigationBehavior». Это свойство имеет два допустимые значения: «подключения» или «путь». Поведение «подключения» описана далее документации.

### Задание пути как rootNavigationBehavior

Задайте значение ```rootNavigationBehavior``` для ```path```и удалите ```requirements``` свойство и выйти из ```path``` свойство как пустую строку. Вы выполнили минимальной конфигурации, необходимые для создания расширения решения. Сохраните файл и воспринять сборки "->" воспринять служат вы бы средства, а затем стороне загрузить расширение в локальном расширения Windows Admin Center.

Массив допустимые манифеста точек входа выглядит следующим образом:
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

Средства, созданных с помощью такой структуры будет необязательно подключений для загрузки, но не будет иметь возможности подключения к узел либо.

### Параметры подключения как rootNavigationBehavior

При задании ```rootNavigationBehavior``` свойства ```connections```, вы указываете оболочке Windows Admin Center, будет присутствовать подключенных узла (всегда сервера какого-либо типа), который он должен устанавливать подключение, и проверить состояние подключения. Эти требования выполнить два действия при проверке подключения. 1) Windows Admin Center будет пытаться создать попытка входа в узел с учетными данными (для запуска в удаленном сеансе PowerShell) и 2) он будет выполняться сценария PowerShell позволяет определить, если узел находится в состоянии, доступный для соединения.

Определение допустимые решение с подключениями будет выглядеть следующим образом:

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

Когда rootNavigationBehavior задано значение «подключения» вам необходимы для построения определения подключений в манифесте. Это включает в себя, свойство «заголовок» (будет использоваться для отображения в ваше решение заголовка, когда пользователь выбирает его в меню), массив connectionTypes (это указывает, какие connectionTypes используются в решении. Подробнее об этом в документации connectionProvider.).

## Включение и отключение меню "Сервис" ##

Другое свойство, доступных в определении решений является свойство «tools». Это будет зависеть от Если отображается меню "Сервис", а также средства, которые будут загружаться. При включении Windows Admin Center будет отображаться в меню Сервис левой руки. С помощью defaultTool, это требуется добавлять точку входа средство в манифест, чтобы обеспечить загружать соответствующие ресурсы. Значение «defaultTool» должно быть свойство «имя» средства, так как он определен в манифесте.
