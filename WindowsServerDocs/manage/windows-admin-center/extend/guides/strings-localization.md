---
title: Строки и локализации в Windows Admin Center
description: Дополнительные сведения о получении к локализации строк в пакете SDK Windows Admin Center (Гонолулу проекта)
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 06/18/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: fb328f86c98141a5a2a1c4fd05ec1d4c96a7bc5f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59845405"
---
# <a name="strings-and-localization-in-windows-admin-center"></a>Строки и локализации в Windows Admin Center #

>Область применения. Windows Admin Center, предварительная версия Windows Admin Center

Перейдем к более подробное руководство расширения пакета SDK для Windows Admin Center и поговорим о строках и локализации.

Обеспечение возможности локализации всех строк, которые отображаются на уровень представления данных, воспользуйтесь преимуществами файла strings.resjson под /src/resources/strings - он уже настроен. Если вам нужно добавить новую строку для расширения, добавьте его в этот файл resjson как новая запись. Существующая структура имеет следующий формат:

``` ts
"<YourExtensionName>_<Component>_<Accessor>": "Your string value goes here.",
```

Можно использовать любой формат, нужный для строк, но имейте в виду, что в процессе создания (процесс, который принимает resjson и выводит можно использовать класс TypeScript) преобразует символ подчеркивания (_) точки (.).

Например, эта запись:
``` ts
"HelloWorld_cim_title": "CIM Component",
```
Создает следующую структуру метода доступа:
``` ts
MsftSme.resourcesStrings<Strings>().HelloWorld.cim.title;
```
