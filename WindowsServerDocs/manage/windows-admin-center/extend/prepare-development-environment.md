---
title: Подготовка среды разработки
description: Подготовка среды разработки пакета SDK для Windows Admin Center (Project Honolulu)
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.localizationpriority: medium
ms.date: 09/18/2018
ms.prod: windows-server-threshold
ms.openlocfilehash: 7b1a0672ee374f3e2d1339c43576db0e5cabdc36
ms.sourcegitcommit: be0144eb59daf3269bebea93cb1c467d67e2d2f1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/20/2018
ms.locfileid: "4080921"
---
# Подготовка среды разработки

>Относится к: Windows Admin Center, ознакомительная версия Windows Admin Center

Давайте приступим к разработке расширений с помощью пакета SDK для Windows Admin Center!  В этом документе мы рассмотрим процесс получения среду вверх и разрабатывать и тестировать расширения для Windows Admin Center.

> [!NOTE]
> Не пользовались ранее пакетом SDK для Windows Admin Center?  Дополнительные сведения о [расширениях для Windows Admin Center](extensibility-overview.md)

Чтобы подготовить среду разработки, выполните следующие действия:

## Установка необходимых компонентов

Чтобы приступить к разработке с помощью пакета SDK, скачайте и установите следующие компоненты:

* [Windows Admin Center](https://aka.ms/WACDownloadPage) (GA или предварительной версии)
* Visual Studio или [Visual Studio Code](http://code.visualstudio.com)
* [Диспетчер пакетов узла](https://npmjs.com/get-npm) (8.12.0 или более поздней версии)
* [NuGet](https://www.nuget.org/downloads) (для публикации расширений)

> [!NOTE]
> Чтобы выполнить действия, описанные ниже, необходимо установить и запустить Windows Admin Center в режиме разработки. Режим разработки позволяет Windows Admin Center загружать неподписанные пакеты расширений.
>
>  Чтобы включить режим разработки, установите Windows Admin Center из командной строки, используя параметр DEV_MODE=1. В приведенном ниже примере замените ```<version>``` на версию, которую вы устанавливаете, то есть ```WindowsAdminCenter1809.msi```.
>
> ```msiexec /i WindowsAdminCenter<version>.msi DEV_MODE=1```

## Установка глобального зависимостей

Затем установите или обновите зависимости, необходимые для проектов, с помощью диспетчера пакетов узла. Эти зависимости установятся глобально и будут доступны для всех проектов.

```
npm install -g npm

npm install -g @angular/cli@1.6.5

npm install -g gulp
npm install -g typescript
npm install -g tslint
npm install -g windows-admin-center-cli
```

>[!NOTE]
>Можно установить более позднюю версию @angular/cli, однако имейте в виду, что если вы устанавливаете версию, больше, чем 1.6.5, вы получите предупреждение на этапе сборки воспринять что версия локального cli не соответствует установленной версии.

## Дальнейшие действия

Теперь, когда подготовки среды, вы готовы приступить к созданию содержимого.

- Создание расширения [Средство](develop-tool.md)
- Создание расширения [Решение](develop-solution.md)
- Создание [подключаемого модуля шлюза](develop-gateway-plugin.md)
- Ознакомьтесь с нашими [руководствами](guides.md)

## Набор средств разработки SDK

Ознакомьтесь с нашей Windows Admin Center [набор средств разработки SDK](https://github.com/Microsoft/windows-admin-center-sdk/blob/master/WindowsAdminCenterDesignToolkit.zip)! Этот набор средств предназначен для поможет вам быстро макет расширений в PowerPoint с помощью Windows Admin Center стили элементов управления и шаблоны страниц. См. в разделе, расширения как могут выглядеть в Windows Admin Center перед началом написания кода!

