---
title: Выбрать другую версию пакета SDK Windows Admin Center
description: Предназначенные для различных версий Windows Admin Center SDK (проект Honolulu)
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 09/18/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: 47ae669e517f963762ee6267594e18f3413a72ff
ms.sourcegitcommit: be0144eb59daf3269bebea93cb1c467d67e2d2f1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/20/2018
ms.locfileid: "4081041"
---
# Выбрать другую версию пакета SDK Windows Admin Center

>Относится к: Windows Admin Center, ознакомительная версия Windows Admin Center

Поддержание в актуальном состоянии с помощью пакета SDK изменений и платформы расширения очень просто.  Мы используем [теги NPM](https://www.npmjs.com/package/@microsoft/windows-admin-center-sdk) упорядочение в выпуске новых функций в версии пакета SDK.

Существует три версии SDK, которые можно выбрать.

* ```latest``` – Этот пакет SDK соответствует текущим Официальным выпуском из Windows Admin Center
* ```insider``` – Этот пакет SDK соответствует текущего выпуска ознакомительная версия Windows Admin Center (доступна в Windows Server Insider Preview)
* ```next``` – Этот пакет SDK содержит самые последние функциональные возможности

> [!NOTE]
> Узнайте подробнее о различных [версий](https://aka.ms/WACDownloadPage) Windows Admin Center, доступные для скачивания.

## Нацеливание версии пакета SDK для нового проекта

При создании нового расширения, вы можете включить ```--version``` параметр предназначенные для различных версий пакета SDK:

```
wac create --company "{!Company Name}" --tool "{!Tool Name}" --version {!version}
```

| Значение | Объяснение | Пример. |
| ----- | ----------- | ------- |
| ```{!Company Name}``` | Название компании (с пробелами) | ```Contoso Inc``` |
| ```{!Tool Name}``` | Ваше средство имя (пробелы) | ```Manage Foo Works``` |
| ```{!version}``` | Версия пакета SDK | ```latest``` |

Ниже приведен пример создания нового расширения предназначенные для ```insider```:

```
wac create --company "Contoso Inc" --tool "Manage Foo Works" --version insider
```

## Нацеливание версии пакета SDK в существующем проекте

Чтобы изменить существующий проект для предназначенные для различных версий пакета SDK, измените следующую строку в ```package.json```:

```
"@microsoft/windows-admin-center-sdk": "latest",
```
В этом примере замените ```latest``` с нужного SDK версии, т. е. ```insider```:

```
"@microsoft/windows-admin-center-sdk": "insider",
```

Затем запустите ```npm install``` обновить ссылки во всем проекте.