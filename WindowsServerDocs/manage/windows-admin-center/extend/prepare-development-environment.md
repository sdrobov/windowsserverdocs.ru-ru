---
title: Подготовка среды разработки
description: Подготовка среды разработки пакета SDK для Windows Admin Center (Project Honolulu)
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.localizationpriority: medium
ms.date: 09/18/2018
ms.prod: windows-server
ms.openlocfilehash: 67bd2a476cedd6d522daeaae54081b02fd893fbd
ms.sourcegitcommit: 083ff9bed4867604dfe1cb42914550da05093d25
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2020
ms.locfileid: "75949978"
---
# <a name="prepare-your-development-environment"></a>Подготовка среды разработки

>Относится к Windows Admin Center, ознакомительной версии Windows Admin Center

Давайте приступим к разработке расширений с помощью пакета SDK для Windows Admin Center!  В этом документе мы расскажем о процессе подготовки и запуска среды для создания и тестирования расширения для центра администрирования Windows.

> [!NOTE]
> Не пользовались ранее пакетом SDK для Windows Admin Center?  Дополнительные сведения о [расширениях для Windows Admin Center](extensibility-overview.md)

Чтобы подготовить среду разработки, выполните следующие действия:

## <a name="install-prerequisites"></a>Установка необходимых компонентов

Чтобы приступить к разработке с помощью пакета SDK, скачайте и установите следующие компоненты:

* [Центр администрирования Windows](https://aka.ms/WACDownloadPage) (общедоступная или предварительная версия)
* Visual Studio или [Visual Studio Code](https://code.visualstudio.com)
* [Диспетчер пакетов node](https://npmjs.com/get-npm) (8.12.0 или более поздней версии)
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
>Вы можете установить более позднюю версию @angular/cli, но имейте в виду, что при установке версии выше 1.6.5 вы получите предупреждение на этапе сборки gulp о том, что локальная версия CLI не соответствует установленной версии.

## <a name="next-steps"></a>Дальнейшие действия

Теперь, когда ваша среда подготовлена, можно приступать к созданию содержимого.

- Создание расширения [Средство](develop-tool.md)
- Создание расширения [Решение](develop-solution.md)
- Создание [подключаемого модуля шлюза](develop-gateway-plugin.md)
- Ознакомьтесь с нашими [руководствами](guides.md)

## <a name="sdk-design-toolkit"></a>Набор средств разработки SDK

Ознакомьтесь с нашим [набором средств разработки пакета SDK](https://github.com/Microsoft/windows-admin-center-sdk/blob/master/WindowsAdminCenterDesignToolkit.zip)для Windows Admin Center! Этот набор средств предназначен для быстрого макетирования расширений в PowerPoint с помощью стилей, элементов управления и шаблонов страниц центра администрирования Windows. Прежде чем приступить к написанию кода, посмотрите, как ваше расширение будет выглядеть в центре администрирования Windows!

