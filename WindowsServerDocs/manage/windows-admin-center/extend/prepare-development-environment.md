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
ms.openlocfilehash: 08634e05d6b7450035324e8d925f2bb9df3b007e
ms.sourcegitcommit: f6490192d686f0a1e0c2ebe471f98e30105c0844
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70869576"
---
# <a name="prepare-your-development-environment"></a>Подготовка среды разработки

>Область применения. Windows Admin Center, ознакомительная версия Windows Admin Center

Давайте приступим к разработке расширений с помощью пакета SDK для Windows Admin Center!  В этом документе мы расскажем о процессе подготовки и запуска среды для создания и тестирования расширения для центра администрирования Windows.

> [!NOTE]
> Не пользовались ранее пакетом SDK для Windows Admin Center?  Дополнительные сведения о [расширениях для Windows Admin Center](extensibility-overview.md)

Чтобы подготовить среду разработки, выполните следующие действия:

## <a name="install-prerequisites"></a>установить необходимые компоненты;

Чтобы приступить к разработке с помощью пакета SDK, скачайте и установите следующие компоненты:

* [Центр администрирования Windows](https://aka.ms/WACDownloadPage) (Общедоступная или предварительная версия)
* Visual Studio или [Visual Studio Code](http://code.visualstudio.com)
* [Диспетчер пакетов узлов](https://npmjs.com/get-npm) (8.12.0 или более поздняя версия)
* [NuGet](https://www.nuget.org/downloads) (для публикации расширений)

> [!NOTE]
> Чтобы выполнить действия, описанные ниже, необходимо установить и запустить Windows Admin Center в режиме разработки. Режим разработки позволяет Windows Admin Center загружать неподписанные пакеты расширений.
>
>  Чтобы включить режим разработки, установите Windows Admin Center из командной строки, используя параметр DEV_MODE=1. В приведенном ниже примере замените ```<version>``` на версию, которую вы устанавливаете, то есть ```WindowsAdminCenter1809.msi```.
>
> ```msiexec /i WindowsAdminCenter<version>.msi DEV_MODE=1```

## <a name="install-global-dependencies"></a>Установка глобальных зависимостей

Затем установите или обновите зависимости, необходимые для проектов, с помощью диспетчера пакетов узлов. Эти зависимости установятся глобально и будут доступны для всех проектов.

```
npm install -g npm

npm install -g @angular/cli@1.6.5

npm install -g gulp
npm install -g typescript
npm install -g tslint
npm install -g windows-admin-center-cli
```

>[!NOTE]
>Вы можете установить более позднюю версию @angular/cli, но имейте в виду, что при установке версии больше 1.6.5 вы получите предупреждение на этапе сборки gulp о том, что локальная версия CLI не соответствует установленной версии.

## <a name="next-steps"></a>Следующие шаги

Теперь, когда ваша среда подготовлена, можно приступать к созданию содержимого.

- Создание расширения [Средство](develop-tool.md)
- Создание расширения [Решение](develop-solution.md)
- Создание [подключаемого модуля шлюза](develop-gateway-plugin.md)
- Ознакомьтесь с нашими [руководствами](guides.md)

## <a name="sdk-design-toolkit"></a>Набор средств разработки SDK

Ознакомьтесь с нашим [набором средств разработки пакета SDK](https://github.com/Microsoft/windows-admin-center-sdk/blob/master/WindowsAdminCenterDesignToolkit.zip)для Windows Admin Center! Этот набор средств предназначен для быстрого макетирования расширений в PowerPoint с помощью стилей, элементов управления и шаблонов страниц центра администрирования Windows. Прежде чем приступить к написанию кода, посмотрите, как ваше расширение будет выглядеть в центре администрирования Windows!

