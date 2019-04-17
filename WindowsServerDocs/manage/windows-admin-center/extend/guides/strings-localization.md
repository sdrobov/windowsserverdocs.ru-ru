---
title: Строки и локализации в Windows Admin Center
description: Сведения о получении готовности к локализации строк в Windows Admin Center SDK (проект Honolulu)
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 06/18/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: f0671160bd790d80e35f6d6c1586a07969939070
ms.sourcegitcommit: f1edfc6525e09dd116b106293f9260123a94de0c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "9296736"
---
# Строки и локализации в Windows Admin Center #

>Относится к: Windows Admin Center, ознакомительная версия Windows Admin Center

Давайте рассмотрим более подробно пакета SDK расширения Windows Admin Center и обсуждать строки и локализации.

Для включения локализации во всех строках, которые отображаются на уровне представления, воспользоваться преимуществами файл strings.resjson под /src/resources/strings - он уже настроен. Если вам необходимо добавить новую строку в расширении, добавьте его в этот файл resjson как новая запись. Существующую структуру соответствует следующий формат:

``` ts
"<YourExtensionName>_<Component>_<Accessor>": "Your string value goes here.",
```

Можно использовать любой формат, который вы хотели строки, но имейте в виду, что процесс создания (процесс, который принимает resjson и выводит можно использовать класс TypeScript) преобразует подчеркивания ("_") для точек (.).

Например этот элемент:
``` ts
"HelloWorld_cim_title": "CIM Component",
```
Создает следующую структуру доступа:
``` ts
MsftSme.resourcesStrings<Strings>().HelloWorld.cim.title;
```

## Добавить дополнительные языки для локализации ## 

Файл strings.resjson локализации для других языков, должен создаваться для каждого языка. Эти файлы должны быть битах ```\loc\output\{!ExtensionName}\{!LanguageFolder}\strings.resjson```. Приведены доступные языки в соответствующие папки.

| Language      | Папка      |
| ------------- |-------------|
| Čeština | cs-CZ |
| Немецкий | de-DE |
| Английский | en-US |
| Испанский | es-ES |
| Français | fr-FR | 
| Magyar | hu-HU | 
| Italiano | it-IT |
| 日本語 | ja-JP | 
| 한국어 | ko-KR | 
| Nederlands | nl-NL |
| Polski | pl-PL |
| Português (Brasil) | pt-BR |
| Português (Португалия) | pt-PT |
| РУССКИЙ | ru-RU |
| Svenska | sv-SE |
| Türkçe    | tr-TR |
| 中文(简体) | zh-CN |
| 中文(繁體) | zh-TW |
> [!NOTE]
> Если вашим потребностям структуры файлов разные внутри loc вывода, необходимо скорректировать localeOffset воспринять задачи «создать resjson-json локализованные», в gulpfile.js. Как в папке loc, его следует начать поиск файлов strings.resjson — это смещение.

Каждый файл strings.resjson будет отформатирован так же, как упоминалось в верхней части в этом руководстве. 

Например, для включения локализации для Испанский включить эту запись в ```\loc\output\HelloWorld\es-ES\strings.resjson```: 
```json
"HelloWorld_cim_title": "CIM Componente",
```
В любое время что добавленном локализованные строки, воспринять создания должен быть выполнен снова для них отображаются. Запустите следующую команду:
``` cmd
gulp generate 
```

Чтобы убедиться, что строки были созданы перейдите к ```\src\app\assets\strings\{!LanguageFolder}\strings.resjson```. Запись только что добавленный будут отображаться в этом файле.
Теперь при переключении вариант языка в Windows Admin Center, вы сможете увидеть локализованные строки в расширении. 
