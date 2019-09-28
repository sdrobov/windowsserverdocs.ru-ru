---
title: Добавление iFrame в расширение средства
description: Разработка расширения инструмента Windows Admin Center SDK (Project Хонолулу) — Добавление iFrame к расширению инструмента
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 09/18/2018
ms.localizationpriority: medium
ms.prod: windows-server
ms.openlocfilehash: 0833b2fd92f2bf4b512120783bb71295a3112745
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71406895"
---
# <a name="add-an-iframe-to-a-tool-extension"></a>Добавление iFrame в расширение средства

>Область применения. Windows Admin Center, ознакомительная версия Windows Admin Center

В этой статье мы добавим iFrame к новому, пустому расширению инструмента, созданному с помощью интерфейса командной строки центра администрирования Windows.

## <a name="prepare-your-environment"></a>Подготовка среды ##

Если вы еще этого не сделали, следуйте указаниям в [подсказке по разработке расширения](../develop-tool.md) для подготовки среды и созданию нового пустого расширения инструмента.

## <a name="add-a-module-to-your-project"></a>Добавление модуля в проект ##

Добавьте новый [пустой модуль](add-module.md) в проект, в который мы добавим IFRAME на следующем шаге.  

## <a name="add-an-iframe-to-your-module"></a>Добавление iFrame в модуль ##

Теперь мы добавим iFrame к новому пустому модулю, который мы только что создали.

В \срк\апп @ no__t-0 перейдите в папку модуля, а затем откройте файл ```{!module-name}.component.html``` и найдите следующее соглашение об именовании:

| Значение | Объяснение | Пример имени файла |
| ----- | ----------- | ------- |
| ```{!module-name}``` | Имя модуля (нижний регистр, пробелы заменены на тире) | ```manage-foo-works-portal.component.html``` |
    
Добавьте следующее содержимое в HTML-файл:

``` html
<div>
  <iframe  style="height: 850px;" src="https://www.bing.com"></iframe>
</div>
```

Вот и вы добавили iFrame к своему расширению.  Затем вы можете [создать и загрузить](../develop-tool.md#build-and-side-load-your-extension) свои расширения в центре администрирования Windows, чтобы увидеть результаты.

> [!Note]
> Параметры политики безопасности содержимого (CSP) могут препятствовать отрисовке некоторых сайтов в iFrame в центре администрирования Windows. Подробнее об этом можно узнать [здесь](https://content-security-policy.com/). 
